# rrpc

A redis rpc implementation.


# Usage


```
from rrpc import RpcServer


rpc = RpcServer('redis://localhost:6379', 'math')


@rpc.task
def add(x, y):
    return x + y


if __name__ == '__main__':
    import sys
    assert len(sys.argv) == 2
    if sys.argv[1] == 'client':
        result = add(1, 2)
        print('add(1, 2) return', result)
        add.delay(3, 4)
    elif sys.argv[1] == 'server':
        rpc.run()
    else:
        raise ValueError('argv[1] should be `client` or `server`')
```
