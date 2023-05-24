
first, let's iterate through each file and subset for what we care about
```
file_headers = ['test1', 'test2']

with open("test.txt") as file1:
    for line in file1:
        if 'USA' in line:
            values = (line.replace('\n', ''))
            df = pd.DataFrame([values.split(' ')], columns=file_headers)
            ## write df to postgres
```

CREATE INDEX users_email ON users(email);
