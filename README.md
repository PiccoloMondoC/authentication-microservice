<h1> authentication-microservice<h1>
<h3> Gen a new keypair</h3>
&nbsp; openssl genpkey -out auth.ed<br>
&nbsp; openssl pkey -in auth.ed -pubout > auth.ed.pub
<h3> try it with a local issuer</h3>
&nbsp; t=$(go run ./cmd/jwt-issue auth.ed)<br>
&nbsp; echo "TOKEN: $t"<br>
&nbsp; go run ./cmd/jwt-validate/ auth.ed.pub $t
<h3>Encryption</h3>
<p style="margin-left: 25px;">To realize security best practices; the code here uses Ed25519 keys.

These are supported by Go but may not work as easily for other languages. However, nearly all the code here is the same regardless of JWT singing method and nothing done here can't be done with other signing algorithms.</p>
