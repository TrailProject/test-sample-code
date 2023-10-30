# Data to be inserted into the file
data_to_insert = """
conf_bucket1
conf_bucket2
conf_bucket3
conf_bucket4
conf_bucket5
conf_bucket6
conf_bucket7
conf_bucket8
conf_bucket9
conf_bucket10
"""

file_dict={
    'conf_bucket1': 'test1',
    'conf_bucket2': 'test2',
    'conf_bucket3': 'test3',
    'conf_bucket4': 'test4',
    'conf_bucket5': 'test5',
    'conf_bucket6': 'test6',
    'conf_bucket7': 'test7',
    'conf_bucket8': 'test8',
    'conf_bucket9': 'test9',
    'conf_bucket10': 'test10'
}

# Writing data to a file
file_path = 'data.txt'  # File path to store the data
with open(file_path, 'w') as file:
    file.write(data_to_insert)

# Reading the data from the file
with open(file_path, 'r') as file:
    retrieved_data = file.read()


with open(file_path, 'r+') as file:
    lines=file.readlines()
    file.seek(0)
    file.truncate()
    for line in lines:
        for i in file_dict.keys():
            if i in line:
                line=line.replace(i,file_dict[i])
        file.write(line)
        print(line, end='')


/*
test1
test2
test3
test4
test5
test6
test7
test8
test9
test10
*/
