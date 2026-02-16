# Random

A utility object class around a similar implementation to UnityEngine.Random and methods

See https://docs.unity3d.com/6000.2/Documentation/ScriptReference/Random.Range.html for more.

Accessing any of the Random properties or calling functions below will internally mutate the random state.

## Class Members

### `Random.new()`
  > Returns `Random`

  > Constructs a Random object with a randomly generated internal state.

### `Random.new(seed)`
  > Returns `Random`

  > Constructs a Random from the provided numeric seed.

### `Random.new(random: Random)`
  > Returns `Random`

  > Constructs a Random from the provided Random.

## Instance Members

### `random.next_float`
  > Returns `number` | **readonly**
  
### `random.next_int`
  > Returns `number` | **readonly**

### `random.value`
  > Returns `number` | **readonly**

### `random:range_float(minInclude: number, maxExclude: number)`
  > Returns `number`

### `random:range_int(minInclude: number, maxExclude: number)`
  > Returns `number`

### `random.inside_unit_circle`
  > Returns `vec2f` | **readonly**

### `random.on_unit_sphere`
  > Returns `vec3f` | **readonly**

### `random.inside_unit_sphere`
  > Returns `vec3f` | **readonly**
