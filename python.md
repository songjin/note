

	from sys import argv
	
	scriptName, firstArgv = argv
	
	file = open(filename)
	content = file.read
	
	file = open(file, 'w')
	file.write("something")
	