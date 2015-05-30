# Are We Taking Open Source For Granted?

Free software. It's not _really_ free. Time, effort, innovation and labor go
into developing the open source projects that we use and often rely on. A lot
of these projects live in the background. Many are known only to those that
look under the hood. But these code bases are the building blocks of the net;
the "dependencies" in our apps and OSs (see the EULA of OS X and you'll see open
source projects listed). Some open source projects find funding through
sales of support, licenses, and/or hosting. But quite a few are just put out
there and sometimes they find their way into the tool boxes of devs and
designers.

When you think about it, how many of the open source projects that you use all
the time are not heavily funded operations? Popular tools like VI/Emacs and tools like
[sed][link_sed] to niche languages like [Tcl][link_tcl] or [Lua][link_lua]
are all entrenched and still active. They may receive funding through the
[Free Software Foundation][link_fsf] and donations, but when was the last time
you paid any money or gave anything back to the developers of that editor, that
library, that module that you always turn to?



## Inspiration

This topic was inspired by an event that occurred [February 5, 2015][link_feb5]. 
The _story_ of an open source project was showcased to the world. The showcase
was not anything special, it was just a blog post and I only learned about it
through a Slashdot RSS. But when GnuPG curator, Werner Koch, wrote a blog
[post][link_koch] breaking down the costs of maintaining that project, he
received a large response. That blog post was made back in December but then
one day the following February, word finally got out. That day over $200K in
donations were pledged to keep the project alive. The largest donations were
made by the [Free Software Foundation's Core Infrastructure
Initiative][link_cii] ($60K), [Facebook][link_gnupg_fb] ($50K), and
[Stripe][link_stripe] ($50K).

Here are some related links:

  - [The call to arms from GnuPG][link_gnupg_blog]
  - [The broader coverage by Slashdot][link_gnupg_slashdot]

## Concerns

GnuPG is only one example of backbone software projects that comprise the core
of the internet's ecosystem. There are many others. A concerning notion is that
in a time when privacy concerns &mdash; brought about by government and overreaching
commercial entities &mdash; is the fact that many secure services are maintained by a
handfull of developers. These secure services are really at the front lines in
defending privacy on the net.  Awesome as these devs are, there is only so much
a few people can do. Bugs exists and no amount of coverage testing is going to
find them _all_ (_Have you every reached 100% coverage on a substantial project?_).

Similar events have occurred. For example, [HeartBleed][link_heartbleed], a bug
found in the TLS implementation of OpenSSL. It surprised many to learn of the
state that codebase was in and that it had a lack of maintainers. So much so
that the [OpenBSD project decided to fork and refactor it][link_openbsd].
Another event to touch entrenched open source code, was [Shell Shock][link_shellshock],
which was a vulnerability in Bash's interpreter.

**What are some other entrenched projects out there that are under funded/under
resourced? What are their stories?**

---

Tags: FOSS, Linux Foundation, Core Infrastructure, Facebook, Stripe

[link_gnupg_blog]: https://gnupg.org/blog/20141214-gnupg-and-g10.html
[link_gnupg_slashdot]: http://it.slashdot.org/story/15/02/05/2243258/gpg-programmer-werner-koch-is-running-out-of-money
[link_gnupg_fb]: https://www.facebook.com/notes/protect-the-graph/supporting-gnu-privacy-guard/1564591893780956
[link_openbsd]: http://www.zdnet.com/article/openbsd-forks-prunes-fixes-openssl/#!
[link_cii]: http://www.linuxfoundation.org/programs/core-infrastructure-initiative
[link_stripe]: https://twitter.com/stripe/status/563449352635432960
[link_heartbleed]: https://en.wikipedia.org/wiki/Heartbleed
[link_lua]: http://lua.org
[link_tcl]: http://tcl.tk
[link_sed]: https://www.gnu.org/software/sed/
[link_koch]:https://gnupg.org/blog/20141214-gnupg-and-g10.html
[link_feb5]: http://www.propublica.org/article/the-worlds-email-encryption-software-relies-on-one-guy-who-is-going-broke
[link_shellshock]: https://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-6271
[link_fsf]: http://fsf.org

