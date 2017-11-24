# Rublix Whitepaper: Internal Magic Sauce

This private github repo relates to the Rublix Whitepaper and describes the
internals of the algorithms of the Proof-of-Ranking algorithm which is applied
to traders using the Rublix platform.

# Ranking function R(t)

Let R(u,t) be the Proof-Of-Rank function describing a user u at a time t.
R(u,t) is a real-valued function where `u=(u\_1,u\_2,...,u\_N)` is an
N-dimensional vector of real values.

    R(u,t) = f(u,w(t))

where w(t) is a real-valued scalar weighting function, independent of the user u, and only
depending on the time t.

# Weighting function

    w(t) = exp(k(t-t\_0)) - 1 for t > t\_0

# License

To Be Determined

# Author

Duke Leto
