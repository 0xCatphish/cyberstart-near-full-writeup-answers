#
# Sample Alien Zip file found at /tmp/alien-zip-2092.zip is password protected
# We have worked out they are using three digit code
# Brute force the Zip file to extract to /tmp
#
# Note: The script can timeout if this occurs try narrowing
# down your search

import zipfile

file_path = "alien-zip-2092.zip"
zipf = zipfile.ZipFile(file_path)


for i in range(999):
    try:
        zipf.extractall('/tmp', pwd=bytes(str(i), encoding='ascii'))
        with open("/tmp/alien-zip-2092.txt", "r") as text:
            print(text.read())
        quit()
    except:
        pass
