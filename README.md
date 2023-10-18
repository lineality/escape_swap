# escape_swap
Avoid escape character issues by swapping around the escape characters before and after other processing.


```


# helper function (escape swap hide)
def swap_hide(file_path):
    """
    avoid escape character problmes
    by removing and restoring escape characters
    before and after file/data processing.

    two functions that work together:
    swap_hide(file_path)
    swap_restore(file_path)
    """
    try:
        # read file
        with open(file_path, 'r', encoding='utf-8-sig') as f:
            raw_text = f.read()

        # remove escape characters with placeholder
        modified_text = raw_text.replace('\\\\', '|||||')

        # remove escape characters with placeholder
        modified_text = raw_text.replace('\\', '^^^^^')

        # write changes to file
        with open(file_path, 'w', encoding='utf-8') as f:  # Change here
            f.write(modified_text)

    except Exception as e:
        e = str(e)
        print(f"Error in swap_hide(file_path) e -> {e}")


# helper function (escape swap restore)
def swap_restore(file_path):
    """
    avoid escape character problmes
    by removing and restoring escape characters
    before and after file/data processing.

    two functions that work together:
    swap_hide(file_path)
    swap_restore(file_path)
    """
    try:
        print(f"swap out -> {file_path}")

        # read file
        with open(file_path, 'r', encoding='utf-8-sig') as f:
            raw_text = f.read()

        # restore escape characters
        modified_text = raw_text.replace('|||||', '\\\\')

        # restore escape characters
        modified_text = raw_text.replace('^^^^^', '\\')

        # write changes to file
        with open(file_path, 'w', encoding='utf-8') as f:  # Change here
            f.write(modified_text)
    except Exception as e:
        e = str(e)
        print(f"Error in swap_restore(file_path) e -> {e}")

```
