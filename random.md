
1. figure out what tables i need
2. design databases
3. iterate through files, subset for what i care about, and load into tables
4. geoencode

first, let's iterate through each file and subset for what we care about
```
file_headers = ['countryID', 'uniqueID']

with open("test.txt") as file1:
    for line in file1:
        if 'USA' in line:
            values = (line.replace('\n', ''))
            df = pd.DataFrame([values.split(' ')], columns=file_headers)
            ## write df to postgres
```

create a temp table that will hold what we temp need
```
CREATE TABLE temp_addresses (
   countryID text
   uniqueID text
   address text
   geohash text
);
```

index the perm table
```
CREATE INDEX idx_addresses_geohash ON addresses(goehash);
```
geohash the temp table and populate the perm table!
