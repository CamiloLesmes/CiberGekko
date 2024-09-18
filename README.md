import requests   # Se usa para importar una biblioteca
import json  # Se usa para que proporcione datos en formato JSON (Creo que cadenas como de texto )

def obtenerIpDesdeDominio(dominio):
    print("------ Dominio -> "+str(dominio)+" ------")
    resultadoBusqueda = requests.get("https://networkcalc.com/api/dns/lookup/"+str(dominio))
    if resultadoBusqueda.json()['records'] != None:
        for i in range(len(resultadoBusqueda.json()['records']['A'])):
            ip = resultadoBusqueda.json()['records']['A'][i]['address']
            resultadoRegion = requests.get("https://ipinfo.io/"+str(ip)+"/json")
            print("La region de la IP -> "+str(ip)+" es "+str(resultadoRegion.json()['region']))
            #En este proceso se obtuvo las direcciones ip de la busqueda de el dominio de la pagina que se utilizo
            #encontrando tambien la region, donde esta ubicada y tdo en un formato ordenado y corto para que se entienda mejor
            #Tambien muestra cuandos dominios tiene la correspondiente pagina web

dominios_empresas  = [    # son los ejemplos de paginas que se tomaron para obtener las ip
    "nintendo.com",        #En estos casos correos o paginas de videojuegos
    "playstation.com",
    "microsoft.com",
    "epicgames.com",
    "activisionblizzard.com",
    "ubisoft.com",
    "ea.com",
    "square-enix.com",
    "capcom.com",
    "bandainamcoent.com",
    "take2games.com",
    "bethesda.net",
    "riotgames.com",
    "valvesoftware.com",
    "cdprojekt.com",
    "sega.com",
    "konami.com",
    "2k.com",
    "rockstargames.com",
    "wbgames.com",
    "giantbomb.com",
    "paradoxinteractive.com",
    "supercell.com",
    "zynga.com",
    "nexon.net",
    "razer.com",
    "gog.com",
    "naughtydog.com",
    "insomniacgames.com",
    "respawn.com",
    "bungie.net",
    "devolverdigital.com",
    "harmonixmusic.com",
    "obsidian.net",
    "treyarch.com",
    "remedygames.com",
    "platinumgames.com",
    "team17.com",
    "fatsharkgames.com",
    "hellogames.org",
    "behaviourinteractive.com",
    "kojimaproductions.com",
    "asobostudio.com",
    "frontier.co.uk",
    "doublefine.com",
    "warframe.com",
    "crytek.com",
    "psyonix.com",
    "hirezstudios.com",
    "arkane-studios.com",
    "tangogameworks.com",
    "ioi.dk",
    "zenimaxonline.com",
    "level5.co.jp",
    "fromsoftware.jp",
    "giantsquidgames.com",
    "thecoalitionstudio.com",
    "bluepointgames.com",
    "supergiantgames.com",
    "bosskey.com",
    "nightschoolstudio.com",
    "camouflaj.com",
    "mediatonic.com",
    "frogwares.com",
    "inxile-entertainment.com",
    "mojang.com",
    "playdead.com",
    "supermassivegames.com",
    "ninjatheory.com",
    "dont-nod.com",
    "dambusterstudios.com",
    "jagex.com",
    "gearboxsoftware.com",
    "neteasegames.com",
    "redbarrelsgames.com",
    "falcom.com",
    "klei.com",
    "owlcatgames.com",
    "telltale.com",
    "theothersidegames.com",
    "gunghoonline.com"
]
#for i in dominios_empresas :
#    obtenerIpDesdeDominio(i)

def obtenerEmailsDesdeDominio(dominio):  # aca se define que se van a obtener correos electronicos desde el/los dominios que se usen
    resultadoEmails = requests.get ("https://api.hunter.io/v2/domain-search?domain="+str(dominio)+"&api_key=41dc41105c0eb4566ceb14d51cfd29faf24e266a")
    print(json.dumps(resultadoEmails.json()['data']['emails'],indent=4))
    if resultadoEmails.json()['data']['emails'] != None:
        for correo in range(len(resultadoEmails.json()['data']['emails'])):
            print("Correo: "+str(resultadoEmails.json()['data']['emails'][correo]['value']))

obtenerEmailsDesdeDominio("riotgames.com") #pagina de donde se tomaron los ip y los correos electronicos

#En el proceso anterior gracias a el Ip de la pagina web que se uso de ejemplo tambien se pudo obtener informacion de algunos
#correos electronicos de personas vinculadas a esa pagina en un formato ordenado de facil entendimiento
#Algunos correos obtenidos son :
#Correo: jsiclari@riotgames.com
#Correo: ehebert@riotgames.com
#Correo: dkim@riotgames.com
#Correo: cschubert@riotgames.com
#Correo: dnabel@riotgames.com
#Correo: lrahal@riotgames.com
#Correo: cgregory@riotgames.com
#Correo: mgoeke@riotgames.com
#Correo: sshrestha@riotgames.com
