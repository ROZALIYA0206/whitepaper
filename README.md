# Rublix Whitepaper: Internal Magic Sauce

This private github repo relates to the Rublix Whitepaper and describes the
internals of the algorithms of the Proof-of-Ranking algorithm which is applied
to traders using the Rublix platform.

# Ranking function R(t)

Let R(u,t) be the Proof-Of-Rank function describing a user u at a time t.
R(u,t) is a real-valued function where `u=(u\_1,u\_2,...,u\_N)` is an
N-dimensional vector of real values.

    R(u,t) = f(u,t, w(t))

where w(t) is a real-valued scalar weighting function, independent of the user u, and only
depending on the time t.

The exact formulation of f(u,t,w(t)) should not be put in the public whitepaper, but we can
give various details about it without giving competitors much.

# Weighting function

The formulatoin should be kept out of public whitepaper.

    w(t) = exp(k(t-t\_0)) - 1 for t > t\_0, k > 0

The weighting function is applied at each time t that a users trades occur, trades that
happened close to t\_0 are weighted close to 0 and trades that happen most recently have
the most weight (exponentially more).

So if a user `u` has 10 trades in the time frame that the ranking algorithm
will use (still undecided, lets call it T), we will need the values w(t) at all
of those 10 times `t\_1 .. t\_10` .

# License

To Be Determined

# Author

Duke Leto
