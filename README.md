from BotAmino import * 
import amino


email = input("email: ")
password = input("pass: ")
client = BotAmino(email=email,password=password)
version = "XD"
print(" bot iniciado = {version}")

cid="137707894"
cidy=137707894


adm=[]

admx=["http://aminoapps.com/p/link1"]


for i in admx:
	try:
		w=client.get_from_code(i).objectId
		adm.append(w)
	except:
		print("invalid admin links/formatos")
subclient=amino.SubClient(comId=cid,profile=client.profile)



@client.event("on_group_member_join")
def on_group_member_join(data):
	if data.comId==cidy:
		try:
			x=data.message.author.icon
			response=requests.get(f"{x}")
			file=open("sample.png","wb")
			file.write(response.content)
			file.close()
			img=open("sample.png","rb")
			subclient.send_message(chatId=data.message.chatId,message=f"""[c][Ic]Bienvenido hermoso.♥︎ <$ {data.message.author.nickname} $> \n
[c]""",embedId=data.message.author.userId,embedTitle=data.message.author.nickname,embedLink=f"ndc://x{cid}/user-profile/{data.message.author.userId}",embedImage=img,mentionUserIds=[data.message.author.userId])
			print(f"disfruta del chat")
		except Exception as e:
			print(e)


@client.event("on_group_member_leave")
def on_group_member_leave(data):
	if data.comId==cidy:
		try:
			subclient.send_message(chatId=data.message.chatId,message="""[c]adiós nadie lo recórdara, ¿quien era ese pibe? ᕕ( ᐛ )ᕗ """)
			print(f"Alguien dejó el chat")
		except Exception as e:
			print(e)
