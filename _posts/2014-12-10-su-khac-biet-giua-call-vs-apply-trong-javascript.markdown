---
layout:     post
title:      "Sự khác nhau giữa function call vs apply trong javascript"
subtitle:   ""
date:       2014-09-24 12:00:00
author:     "Mặt Mụn"
level:		"Chunin"
---

<code>
	fun.call(thisArg[, arg1[, arg2[, ...]]])
</code>

<code>
	fun.apply(thisArg[, argsArray])
</code>

Hai function trên chỉ khác nhau ở cách truyền tham số khi gọi chúng.
Cả 2 function đều có tham số đầu tiên là *thisArg* (còn cái này là cái chi chi nếu bạn nào chưa hiểu có thể tham khảo tại đây nhé <a href="http://bjorn.tipling.com/all-this">all-this</a>)

Về phần đối số tiếp theo, thì *fun.call* sẽ truyền các tham số theo dạng danh sách, còn *fun.apply* sẽ truyền các tham số dưới dạng 1 mảng đơn các tham số (vậy chi *fun.apply* chỉ cần có 2 tham số chính).

Ví dụ:

# fun.call
<script src="https://gist.github.com/ninja-saigon/c98448dee975cbd1202d.js"></script>

#fun.apply
<script src="https://gist.github.com/ninja-saigon/05bde13cfa687c18871d.js"></script>