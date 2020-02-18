There is a vulnerability in the FreelancerBooks v1.0 that allows a crafted page to reset the password of an arbitrary user.

There is a "random" value included as part of the request, but you can just generate the CSRF HTML without that value
and the password will still be changed.
