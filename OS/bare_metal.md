### <u>Inline Function</u>
By declaring a function inline, you can direct GCC to make calls to that function faster. One way GCC can achieve this is to integrate that function’s code into the code for its callers. This makes execution faster by eliminating the function-call overhead; in addition, if any of the actual argument values are constant, their known values may permit simplifications at compile time so that not all of the inline function’s code needs to be included. The effect on code size is less predictable; object code may be larger or smaller with function inlining, depending on the particular case. You can also direct GCC to try to integrate all “simple enough” functions into their callers with the option

```C
static inline int
inc (int *a)
{
  return (*a)++;
}
```
