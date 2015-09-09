# Kwesi v.0.1 alpha
Computational graph library for machine learning in Julia


#### Usage

Here's an implementation of this computational graph (<a href="http://colah.github.io/posts/2015-08-Backprop/">source</a>)
<img src="http://colah.github.io/posts/2015-08-Backprop/img/tree-eval.png" width="400px" />

```Julia
using Kwesi

function addone(b)
  b + 1
end
function addxy(x,y)
  x + y
end
function multxy(x,y)     
  x * y
end

a = VarNode("a", [2])
b = VarNode("b", [1])
c = OpsNode(addxy, [0], [a,b])
d = OpsNode(addone, [0], [b])
e = OpsNode(multxy, [0], [c,d])
println(runNode(e))
println("d state is " * string(d.state))
```
```bash
Real[6]
d state is Real[6]
```