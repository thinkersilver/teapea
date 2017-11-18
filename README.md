## Teepee 

![](/images/teepee.png)


Teepee is a tiny utility library that creates data driven documents.
### Install 

Clone the repo 
``` git clone  thinkersilver/teepee```

or download from the releases tab then type: 

``` python setup.py install  ```

### Getting Started 

Get Fabric from teepee
```
from teepee import Fabric
```

and ***weave*** your data into your templates (fabric) and then ***render*** 

 
1. Create your data: 

```markdown
names =[] 
names.append([("name",'bob'),("age",22)])
names.append([("name",'terry'),("age",21)])
names.append([("name",'gordon'),("age",23)])

data = [ dict(e) for e in names ]
```
2. add your root node:

```
f = Fabric()
f.add_weave("$/root","""

#addresses
""",lambda : {"addresses":data})
f.add_weave("$/root/addresses",""" * #name is  #age years old \n""")


```

3. Then render
```
print f.render("$/root")
```


