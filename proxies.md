# Proxies

A _Proxy_ proxies access to another object through its use of _traps_. It offers different kind of traps, for example `get` and `set`.

    // Proxied Object
    const alpha = {
      name: 'abc'
    }

    // Proxy Object
    const beta = new Proxy(alpha, {
      get: (target, key) => {
        return key in target ? target[key] : 'No key'
      },
      set: (target, key, value) => {
        target[key] = value;
        return true;
      }
    })

    // Access existing property
    alpha.name // `abc`
    beta.name // `abc`

    // Change existing property
    beta.name = 'def';
    alpha.name // `def`
    beta.name // `def`

    // Access non-existant property
    alpha.nope // undefined
    beta.nope // 'No key'

    // Add new property via proxy
    beta.nope = 'ghi';
    alpha.nope; // ghi
    beta.nope // ghi



