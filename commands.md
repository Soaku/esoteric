# Commands

List of commands available in Pepe.

- Click the section title to view corresponding column in [the project](https://github.com/Soaku/Pepe/projects/2).
- Click the command name to view corresponding note in [the project](https://github.com/Soaku/Pepe/projects/2).
- `Stack <<` - Push to stack
- `Stack >>` - Pop **selected item** from the stack and perform action on the popped item.
- Pushed items always go to the end of stack and they don't change pointer location.

[Preserve]: https://github.com/Soaku/Pepe/projects/4#card-10518943
[Insert]: https://github.com/Soaku/Pepe/projects/4#card-10519066
[Prepend]: https://github.com/Soaku/Pepe/projects/4#card-10519078
[PopPush]: https://github.com/Soaku/Pepe/projects/4#card-10520673
[PreservePush]: https://github.com/Soaku/Pepe/projects/4#card-10520695

### [1 E/e (2) Basic stack operations](https://github.com/Soaku/Pepe/projects/2#column-2205663)

- > Flags:
  > r = [Insert],
  > R = [Prepend]
  - `E` - [WS << push 0](https://github.com/Soaku/Pepe/projects/2#card-7485469)
- `e` - [WS >> Do nothing (pop)](https://github.com/Soaku/Pepe/projects/2#card-7485481)

### [2 E/e (4) Program flow](https://github.com/Soaku/Pepe/projects/2#column-2172199)

> For every command in section: X is value of the selected item from WS.
>
> Goto commands don't do anything if corresponding labels don't exist.
>
> Commands in this section do not pop.
>
> Flags are listed in a [project column](https://github.com/Soaku/Pepe/projects/4#column-2890828)

- `EE` - [Create label with name X](https://github.com/Soaku/Pepe/projects/2#card-7338713)
  - Calling again with the same name will result in replacing previous label
- `Ee` - [Return to where a goto was called last](https://github.com/Soaku/Pepe/projects/2#card-7339434)
- `eE` - [Goto label X if active item == active item in the other stack](https://github.com/Soaku/Pepe/projects/2#card-7716208)
- `ee` - [Goto label X if active item != active item in the other stack](https://github.com/Soaku/Pepe/projects/2#card-7716960)

### [3 E/e (8) I/O](https://github.com/Soaku/Pepe/projects/2#column-2171797)

> If input is a string, every contained byte is pushed as an integer
>
> **WARNING** - Pepe has multiple inputs support. Calling an input-taking
> function will move the "input pointer" to the next value

- > Flags:
  > r = [Insert],
  > R = [Prepend]
   - `EEE` - [WS << Auto-parse input](https://github.com/Soaku/Pepe/projects/2#card-7337865)
   - `EEe` - [WS << Parse input as string](https://github.com/Soaku/Pepe/projects/2#card-7337875)
   - `EeE` - [WS << Parse input as integer](https://github.com/Soaku/Pepe/projects/2#card-7485918)
   - `Eee` - [WS << Parse input as float](https://github.com/Soaku/Pepe/projects/2#card-7337874)
- > Flags:
  > r = [Preserve]
   - `eEE` - [WS >> Output as number](https://github.com/Soaku/Pepe/projects/2#card-7344002)
   - `eEe` - [WS >> Output as character](https://github.com/Soaku/Pepe/projects/2#card-7337895)
- `eeE` - [Output newline (`\n`)](https://github.com/Soaku/Pepe/projects/2#card-7501362)
- `eee` - [Output WS content as string without popping](https://github.com/Soaku/Pepe/projects/2#card-7493465)

### [4 E/e (16) Pointer](https://github.com/Soaku/Pepe/projects/2#column-2171962)

*1 slot left*

- `EEEE` - [Move WS pointer to first item](https://github.com/Soaku/Pepe/projects/2#card-7337904)
- `EEEe` - [Move WS pointer to last item](https://github.com/Soaku/Pepe/projects/2#card-7337939)
- `EEeE` - [Rewind - Move WS pointer to previous item](https://github.com/Soaku/Pepe/projects/2#card-7337914)
- `EEee` - [Forward - Move WS pointer to next item](https://github.com/Soaku/Pepe/projects/2#card-7337906)
- `EeEE` - [Set position to random item](https://github.com/Soaku/Pepe/projects/2#card-7487437)
- `EeEe` - Empty (reserved for random function)
- `EeeE` - [Push pointer position (0-indexed)][i10]
- `Eeee` - [Push pointer position in reverse][i10]
- `eEEE` - [Move input pointer to the first item][i10]
- `eEEe` - [Move input pointer to the last item][i10]
- `eEeE` - [Move input pointer to the previous item][i10]
- `eEee` - [Move input pointer to the next item][i10]
- `eeEE` - [Push input pointer position][i10]
- `eeEe` - [Push amount of input items left][i10]
  - Warning: this will return a negative number if end of input was crossed.
- `eeeE` - [Lock input pointer – prevent automatic changes to it][i10]
- `eeee` - [Unlock input pointer – allow automatic changes to it][i10]

[i10]: https://github.com/Soaku/Pepe/issues/10

### [5 E/e (32) Active item](https://github.com/Soaku/Pepe/projects/2#column-2173896)

*12 slots left*

- > Flags:
  > r = [PopPush],
  > R = [PreservePush]
   - `EEEEE` - [Increment active item](https://github.com/Soaku/Pepe/projects/2#card-7338659)
   - `EEEEe` - [Decrement active item](https://github.com/Soaku/Pepe/projects/2#card-7338662)
- `EEEeE` - *Deprecated* [Duplicate active item (duplicate to next)](https://github.com/Soaku/Pepe/projects/2#card-7338639)
- > Flags:
  > r = [Insert],
  > R = [Prepend]
   - `EEEee` - [Push active item (duplicate to end)](https://github.com/Soaku/Pepe/projects/2#card-7338640)
- > Flags:
  > r = [PopPush],
  > R = [PreservePush]
   - `EEeEE` - [Random from 0 to active item value](https://github.com/Soaku/Pepe/projects/2#card-7486911)
   - `EEeEe` - [Random from 1 to active item value](https://github.com/Soaku/Pepe/issues/18)
   - `EEeeE` - [Round active item](https://github.com/Soaku/Pepe/projects/2#card-7344007)
   - `EEeee` - [Round active item to 0.5](https://github.com/Soaku/Pepe/projects/2#card-7487731)
   - `EeEEE` - [Ceil active item](https://github.com/Soaku/Pepe/projects/2#card-7344020)
   - `EeEEe` - [Floor active item](https://github.com/Soaku/Pepe/projects/2#card-7344011)
   - `EeEeE` - [Absolute value of active item](https://github.com/Soaku/Pepe/projects/2#card-7485569)
   - `EeEee` - [Reverse sign of active item (times -1)](https://github.com/Soaku/Pepe/projects/2#card-7344091)
   - `EeeEE` - [Square - Raise active item to second power](https://github.com/Soaku/Pepe/projects/2#card-7487657)
   - `EeeEe` - [Cube - Raise active item to third power](https://github.com/Soaku/Pepe/projects/2#card-7487662)
   - `EeeeE` - [Square root of active item](https://github.com/Soaku/Pepe/projects/2#card-7488241)
   - `Eeeee` - [Cube root of active item](https://github.com/Soaku/Pepe/projects/2#card-7488346)
   - `eEEEE` - [Modulo 2 of active item](https://github.com/Soaku/Pepe/projects/2#card-7708043)
   - `eEEEe` - [Modulo 3 of active item](https://github.com/Soaku/Pepe/projects/2#card-7708024)
   - `eEEeE` - [Active item << 1](https://github.com/Soaku/Pepe/projects/2#card-13368193)
   - `eEEee` - [Active item >>> 1](https://github.com/Soaku/Pepe/projects/2#card-13368228)

### [6 E/e (64) 2 value](https://github.com/Soaku/Pepe/projects/2#column-2172019)

*49 slots left*

> Commands operating on active items from both stacks.
>
> A = active item from WS, B = active item from the other stack

> All commands here support the flags:
>
> r = [Preserve], \
> R = Empty,      \
> rr = [Insert],  \
> rR = [Prepend], \
> Rr = [Insert] & [Preserve], \
> RR = [Prepend] & [Preserve]

- `EEEEEE` - [WS << A+B](https://github.com/Soaku/Pepe/projects/2#card-7338110)
- `EEEEEe` - [WS << A-B](https://github.com/Soaku/Pepe/projects/2#card-7338448)
- `EEEEeE` - [WS << A\*B](https://github.com/Soaku/Pepe/projects/2#card-7338506)
- `EEEEee` - [WS << A/B](https://github.com/Soaku/Pepe/projects/2#card-7338512)
- `EEEeEE` - [WS << str(A)+str(B)](https://github.com/Soaku/Pepe/projects/2#card-7487145)
- `EEEeEe` - [WS << A split every B digit](https://github.com/Soaku/Pepe/projects/2#card-7492924)
- `EEEeeE` - [WS << B chunks of A](https://github.com/Soaku/Pepe/projects/2#card-7492793)
- `EEEeee` - Empty
- `EEeEEE` - [WS << A^B](https://github.com/Soaku/Pepe/projects/2#card-7487563)
- `EEeEEe` - [WS << B'th root of A](https://github.com/Soaku/Pepe/projects/2#card-7487580)
- `EEeEeE` - [WS << A%B (modulo)](https://github.com/Soaku/Pepe/projects/2#card-7708060)
- `EEeEee` - Empty
- `EEeeEE` - [Left bit shift](https://github.com/Soaku/Pepe/projects/2#card-13368042)
- `EEeeEe` - [Logical right bit shift](https://github.com/Soaku/Pepe/projects/2#card-13368119)
- `EEeeeE` - [WS << Character repeated B times.](https://github.com/Soaku/Pepe/issues/12)
- `EEeeee` - Empty
- `EeEEEE` - [WS << Random number A...B (inclusive)](https://github.com/Soaku/Pepe/issues/18)
- `EeEEEe` - [WS << Random number A..B (exclusive)](https://github.com/Soaku/Pepe/issues/18)
- `EeEEeE` - [WS << Greater number (max) of A and B](https://github.com/Soaku/Pepe/issues/19)
- `EeEEee` - [WS << Lower number (min) of A and B](https://github.com/Soaku/Pepe/issues/19)

### [7 E/e (128) Cross-stack](https://github.com/Soaku/Pepe/projects/2#column-2172008)

*121 slots left*

- > Flags:
  > r = [Insert],
  > R = [Prepend]
    - `EEEEEEE` - [Move active item to the other stack](https://github.com/Soaku/Pepe/projects/2#card-7338040)
    - `EEEEEEe` - [Copy active item to the other stack](https://github.com/Soaku/Pepe/projects/2#card-7338048)
    - `EEEEEeE` - [Move WS content to the other stack](https://github.com/Soaku/Pepe/projects/2#card-7338051)
    - `EEEEEee` - [Copy WS content to the other stack](https://github.com/Soaku/Pepe/projects/2#card-7338052)
- `EEEEeEE` - [Reverse stack names (R = r; r = R)](https://github.com/Soaku/Pepe/projects/2#card-7344098)
- `EEEEeEe` - Empty
- `EEEEeeE` - [Diff - Remove items from WS that occur in the other stack](https://github.com/Soaku/Pepe/projects/2#card-7487263)
- `EEEEeee` - [Reverse diff - Remove items from wS that **don't** occur in the other stack](https://github.com/Soaku/Pepe/projects/2#card-7487284)

### [8 E/e (256) Full stack](https://github.com/Soaku/Pepe/projects/2#column-2172176)

*246 slots left*

> Commands operating on the whole stack


- > Flags: \
  > r = [Preserve], \
  > R = Empty,      \
  > rr = [Insert],  \
  > rR = [Prepend], \
  > Rr = [Insert] & [Preserve], \
  > RR = [Prepend] & [Preserve]
    - `EEEEEEEE` - [Sum (+)](https://github.com/Soaku/Pepe/projects/2#card-7338609)
    - `EEEEEEEe` - Empty
    - `EEEEEEeE` - [Product (\*)](https://github.com/Soaku/Pepe/projects/2#card-7338613)
    - `EEEEEEee` -  Empty
    - `EEEEEeEE` - [Join](https://github.com/Soaku/Pepe/projects/2#card-7338617)
    - `EEEEEeEe` - Empty
- `EEEEEeeE` - [Increment all](https://github.com/Soaku/Pepe/projects/2#card-7338669)
- `EEEEEeee` - [Decrement all](https://github.com/Soaku/Pepe/projects/2#card-7338670)
- `EEEEeEEE` - [Clear](https://github.com/Soaku/Pepe/projects/2#card-7338687)
- `EEEEeEEe` - [Clear, but don't remove selected item](https://github.com/Soaku/Pepe/projects/2#card-7488515)
- `EEEEeEeE` - [Sort](https://github.com/Soaku/Pepe/projects/2#card-7488771)
- `EEEEeEee` - [Reverse order](https://github.com/Soaku/Pepe/projects/2#card-7344092)
- `EEEEeeEE` - [Shuffle order](https://github.com/Soaku/Pepe/projects/2#card-7487499)
- `EEEEeeEe` - Reserved for an order-changing function
- `EEEEeeeE` - [Greatest number in the stack (max)](https://github.com/Soaku/Pepe/issues/19)
- `EEEEeeee` - [Lowest number in the stack (min)](https://github.com/Soaku/Pepe/issues/19)

### [9 E/e (512) Characters](https://github.com/Soaku/Pepe/projects/2#column-2205901)

First letter:

- `E` - Push
- `e` - Print as character

Following letters are parsed as:

- `E` - 1
- `e` - 0

Converted to a binary number, then to a corresponding ASCII character.

Ex: To print `A`, the command would be `reEeeeeeeE`.

> Supported flags:
>
> r = [Insert]
> R = [Prepend]
