# Go-Upload-Files-FTP
		conn, err := ftp.Connect("youIPaddress", 21)
		if err != nil {
			fmt.Println("no connection, error:", err)
			return
		}
		defer conn.Close()

		err = conn.Login("username", "password")
		if err != nil {
			fmt.Println("login failed, error:", err)
			return
		}
		defer conn.Quit()

		//Example, Open file in RDONLY mdoe from users Desktop
		source, _ := os.OpenFile("c:\\%username$\\Desktop\\YourFile, os.O_RDONLY, 0644)
		err = conn.Upload(source, "/FilenameonFTPserver")
		if err != nil {
			fmt.Println("error on uploading file, error:", err)
		}
