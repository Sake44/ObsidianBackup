A user’s first instinct might be to use more positional variables such as $2, $3 and so on.
Unfortunately, we can’t anticipate the number of arguments that a user might choose to use. To solve this issue, it will be helpful to introduce more built-in variables.

```

#!/bin/bash

# a friendly script to greet users
if [ $# -eq 0 ]
then
echo "Please enter at least one user to greet."
exit 1

else
echo "Hello $@!"
exit 0
fi
```

Bash will parse the arguments, and separate each argument when it encounters a space between them. The content look like an array. [[For Loops]]
