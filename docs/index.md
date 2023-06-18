# Home

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.

### Codeblock test

``` py title="Code to solve remove element from list" linenums="1"
def removeElement(nums, val):
    """
    Using one loop and two pointers
    Don't preserve order
    """

    # Remove the elment from the list
    i = 0
    j = len(nums) - 1
    count = 0

    while i < j:
        if nums[i] == val:
            while j > i and nums[j] == val:
                j -= 1
            print('i:', i, 'j:', j)
            # swap elements
            temp = nums[i]
            nums[i] = nums[j]
            nums[j] = temp
            count += 1
            print(nums)
        i += 1

    if count == 0:
        j = j + 1
    return j


def main():
    arr = [int(j) for j in input().split()]
    val = int(input())
    ans = removeElement(arr, val)
    print(ans)
    print(arr[:ans])


if __name__ == '__main__':
    main()
```
