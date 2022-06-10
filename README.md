# je
je - json explore tool

je is a tool to dynamically explore a json file. It allows to quickly view its structure, without having to open it manually.

## Usage

To explore a file, run `je <file.json>``

You then enter a command line interface to explore your json.

Available commands:
- `?`: show available commands
- `keys` or `k` - print all keys of a dictionnary
- `.<key>` - go to a specific key. Example: .foo for a dict like {'foo': 'bar'}
- `<int>` - go to a specific index of a list. Example: `4`
- `print` or p - print the current value. Warning, it might print a lot of data
- `up` or u - go up one level in the tree
- `quit` or q - quit the program

For example, let's consider a file containing: 
```
{
    "foo": "bar",
    "example": [1, 2, 3],
    "test": {"hello": "world"},
}
```

```
$ je test.json
Dict[3]
Keys:  dict_keys(['foo', 'example', 'test'])
Press ? to get help
 > keys
dict_keys(['foo', 'example', 'test'])
 > .foo
str
foo > p
bar
foo > u
Dict[3]
Keys:  dict_keys(['foo', 'example', 'test'])
 > .example
List[3]
example > p
[1, 2, 3]
example > 0
int
example.0 > p
1
example.0 > u
List[3]
example > u
Dict[3]
Keys:  dict_keys(['foo', 'example', 'test'])
 > .test
Dict[1]
Keys:  dict_keys(['hello'])
test > p
{'hello': 'world'}
```
