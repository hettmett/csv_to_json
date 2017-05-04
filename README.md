# csv_to_json
Converting hierarchical data stored in csv like file to python dict/json. This solution is related to the issue posted at stackoverflow: http://stackoverflow.com/questions/43757965/convert-csv-to-json-tree-structure

Using [defaultdict](https://docs.python.org/2/library/collections.html#collections.defaultdict) from the [collections](https://docs.python.org/2/library/collections.html#module-collections) standard library is making a lot of problems with hierarchical structures easy and solvable. Here's developed a sample solution for the problem. But before running the script, please, make sure you have comma separated csv file (named test.csv) or you can change the [csv reader](https://docs.python.org/3.5/library/csv.html#module-csv) logic down there.

Here's the csv file I've tested the script on:

```
condition, target, sub, dub
oxygen,tree,G1,T1
oxygen,tree,G2,T1
oxygen,tree,G2,T2
water,car,G3,T1
water,tree,GZ,T1
water,tree,GZ,T2
fire,car,GTD,T3
oxygen,bomb,GYYS,T1
```

Technically the script should work for any kind of csv file, with various dimensions. But you need to test it by yourself to be sure.

And here's the json segment from the result:

```
{
    "name": "oxygen",
    "children": [
      {
        "name": "tree",
        "children": [
          {
            "name": "G2",
            "children": [
              {
                "name": "T2"
              },
              {
                "name": "T1"
              }
            ]
          },
          {
            "name": "G1",
            "children": [
              {
                "name": "T1"
              }
            ]
          }
        ]
      },
      {
        "name": "bomb",
        "children": [
          {
            "name": "GYYS",
            "children": [
              {
                "name": "T1"
              }
            ]
          }
        ]
      }
    ]
  }
```

Happy pythonning ;)
