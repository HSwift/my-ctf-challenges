# insane-xss

N1CTF 2024 web challenge

## 起源

之前在网上冲浪的时候发现了一个很有意思的洞"[CVE-2024-21733](https://nvd.nist.gov/vuln/detail/cve-2024-21733)"，这个洞是一个Tomcat的请求走私。但实际复现之后发现它并不是传统意义上由于前后端对协议处理不一致造成的走私，而是一种缓冲区溢出（可能也不是很准确）。

不过后来这个idea被WMCTF抢先了[PasswdStealer](https://blog.wm-team.cn/index.php/archives/80/#PasswdStealer)，他的题目思路确实比我预先设想的要好，在SpringBoot的场景下利用`StandardMultipartHttpServletRequest.parseRequest -> MultipartStream.skipPreamble`自动读取body的功能，实现了在裸SpringBoot下的利用。

## 剩下的有点懒得写了

网上已经有一些关于 CVE-2024-21733 的分析了，就原谅我咕咕咕吧。