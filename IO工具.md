
#文件写入
	string path = @"c:\temp\MyTest.txt";   //文件路径
            if (!File.Exists(path))			//是否存在该文件
            {
                // Create a file to write to.
                using (StreamWriter sw = File.CreateText(path))  //创建文件并写入信息
                {
                    sw.WriteLine("Hello");				//输入一行数据
                    sw.WriteLine("And");
                    sw.WriteLine("Welcome");
                }
            }

#读取文件
            using (StreamReader sr = File.OpenText(path))  //将文件打开读取
            {
                string s = "";
                while ((s = sr.ReadLine()) != null)			//如果下一行不为空就一直往下读取
                {
                    Console.WriteLine(s);
                }
            }

#复制文件
	File.Copy(path, path2);   //将路径为参数1的文件数据复制到参数2文件路径中

#删除指定路径文件
	File.Delete(path2);

#获取指定路径下文件名
	var txtFiles = Directory.EnumerateFiles(sourceDirectory, "*.txt");		//获取指定路径下所有.txt文件
                foreach (string currentFile in txtFiles)
                {
                    string fileName = currentFile.Substring(sourceDirectory.Length + 1);  //获取该路径下的文件名   
                    Directory.Move(currentFile, Path.Combine(archiveDirectory, fileName)); //指定该文件移动到指定的文件目录下

                }