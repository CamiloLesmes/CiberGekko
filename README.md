import requests
import json

class usersInfo:

    def __init__(self):
        self.listUsers = []
        pass

    def getUsers(self):
        responseUsers = requests.get("https://datos.gov.co/resource/jtnk-dmga.json")
        dataJson = responseUsers.json()
        for ind in range(len(responseUsers.json())):
            print(responseUsers.json()[ind]['email_address'])
            self.listUsers.append(dataJson[ind]['email_address'])

def validateUsers(self):
    for email in self.listUsers:

prueba = usersInfo()
prueba.getUsers()
