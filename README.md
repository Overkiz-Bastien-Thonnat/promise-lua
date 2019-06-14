# promise-lua
[Promises/A+](https://promisesaplus.com/) implemented in Lua language.

## Installation
You can install promise-lua using [LuaRocks](https://luarocks.org/modules/pyericz/promise-lua):
```
$ luarocks install promise-lua
```

## Usage
```lua
local setTimeout = ... -- An async function
local Promise = require 'promise'

Promise(function(resolve, reject)
  setTimeout(function()
    local num = math.random(10)
    if num % 2 == 0 then
      resolve(num)
    else
      reject(num)
    end
  end, 1000)
end):thenCall(function(value)
  print('an even number', value)
end):catch(function(value)
  print('an odd number', value)
end):finally(function()
  print('all done')
end)
```

## License
[MIT License](https://github.com/pyericz/promise-lua/blob/master/LICENSE)
