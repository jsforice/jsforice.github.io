---
layout:     post
title:      "Backbonejs và Requirejs basic"
subtitle:   "Hướng dẫn sử dụng cơ bản BackboneJs và RequireJs"
date:       2014-09-24 12:00:00
author:     "Mặt Mụn"
level:		"Chunin"
---

<p>Như hướng dẫn lần trước chúng ta đã có thể xây dựng được todo app đơn giản chỉ sử dụng backbonejs.<br/> Hầu hết các đối tượng như model, view, collection đều được khai báo thông qua một file javascript duy nhất (main.js), đối với 1 todo app nhỏ thì nhiêu đây là đủ.</p>
<p>Nhưng giả sử bạn có một app với mức độ phức tạp hơn, phải chia ra từng module nhỏ, mỗi module lại có thể chia sẽ model, collection cho các module khác.</p>

Ví dụ giờ nếu todo app của chúng ta yêu cầu phải login để vào app, vậy chúng ta sẽ có 1 page #login, 1 page #todo.

Một số resource sẽ được sử dụng như: 

- page #login: UserModel, LoginView
- page #todo: UserModel, TodoModel, TodoView, TodoCollection, ...

Ở đây mình sẽ không defined toàn bộ resource vào 1 file js nữa, mà mình sẽ chia ra từng file js nhỏ như: user_model.js, login_view.js, ....

Đối với page #login mình sẽ include từng resource cần thiết vào như sau:

{% highlight html linenos %}
<script src="js/jquery.js"></script>
<script src="js/underscore.js"></script>
<script src="js/backbone.js"></script>
<script src="js/user_model.js"></script>
<script src="js/login_view.js"></script>
<script src="js/main.js"></script>
{% endhighlight %}

Mình vẫn thực hiện tương tự đối với page #todo.
Ở đây mình vẫn phải chú ý thứ tự các script load sao cho đúng (thiệt là mệt).

Nếu chúng ta sử dụng requirejs thì có khá hơn được tí tẹo nào hem ???

Kq: nếu sử dụng requirejs thì trong file html của chúng ta chỉ cần include script như thế này là đủ:
{% highlight html linenos %}
<script data-main="main" src="js/requirejs.js"></script>
{% endhighlight %}

WTF ?

<script <b>data-main="js/main"</b> src="js/requirejs.js"></script>

Requirejs sẽ tự động load script js/main.js

{% highlight javascript linenos %}
// Require main app viewer
require([
	'js/jquery',
	'js/backbone',
	'js/underscore',
	'js/user_model',
	'js/login_view'
], function($, Backbone, _, UserModel, LoginView){
	// New loign view instance
	var loginView = new LoginView({el: '#todo'});
		loginView.render(); // Render login view
});
{% endhighlight %}