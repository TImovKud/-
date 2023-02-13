# -def read_from_file(filename):
    file = open(filename, 'r')
    names = tuple(file.readline()[:-1].split(','))
    data = []
    for line in file:
        line = line.split(',')
        data.append((int(line[0]), str(line[1]), line[2], int(line[3]), int(line[4]), int(line[5])))
    return names, data


def write_to_file(filename):
    with open(filename, 'w') as file:
        file.write(','.join(names)+'\n')
        for line in data:
            line = [str(i) for i in line]
            file.write(','.join(line)+'\n')
        print("Ввести данные?")
        print("1) Yes")
        print("2) No")
        answer = input()
        if answer == '1':
            new_data(filename)
        else:
            exit()

def new_data(file_name):
    new_data = []
    i = 0
    while i <= 5:
        new = input()
        new_data.append(new)
        i += 1
    with open(file_name, 'w') as file:
        file.write(','.join(names)+'\n')
        for line in data:
            line = [str(i) for i in line]
            file.write(','.join(line)+'\n')
        file.write(','.join(new_data) + '\n')

names, data = read_from_file('data.csv')
print(names,data)
write_to_file('data.csv')
