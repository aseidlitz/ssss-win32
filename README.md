## SSSS: Shamir's Secret Sharing Scheme (Windows port)


**WARNING:** This is an outdated and insecure SSSS port preserved purely for historic reasons

Shamir's Secret Sharing Scheme is used to securely share certain secret information (e.g. root password or list of passwords) between a group of people in such way, so that at least two (or more) of them need to combine their shares to recreate the original secret. Its a handy way to protect sensitive passwords without giving them to anybody in particular.

This is my quick and dirty port of ssss utility by B. Poettering to Windows. It doesn't depend on Cygwin DLL at runtime, but requires GMP and RandomKit to compile.

I tried to build it from the original source with both Cygwin and MINGW, but was running in all sorts of problems. One of challenges was /dev/random which dind't work as expected. I had to hack it out and replace by a different source of entropy (taken from Randomkit). It's ugly, but it works.

**CAUTION:** RandomKit uses a MersenneTwister RNG as its kernel. This is not a cryptographically secure random number generator. But RandomKit seeds its Mersenne Twister initially with /dev/random entropy (and the seed is quite large). The overall security of this design remains arguable.

The source needs to be updated to use Windows CryptoAPI to seed RNG, as suggested by B.Pottering, and more cryptographically sound RNG (Blum, Blum & Shub in particular).

The homepage for the original UNIX version of ssss by B. Poettering: http://point-at-infinity.org/ssss/

Wikipedia's article about Secret Sharing: http://en.wikipedia.org/wiki/Secret_sharing


### Binaries

Binaries (both are the same executable with two different names):

 * ssss-split.exe (59.5 KB) MD5 = 07 21 d1 f3 f7 0b 4a 8e bb be e5 19 18 3d 90 65

 * ssss-combine.exe (59.5 KB) MD5 = 07 21 d1 f3 f7 0b 4a 8e bb be e5 19 18 3d 90 65
