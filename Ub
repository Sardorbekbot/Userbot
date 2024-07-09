from telethon import TelegramClient, events, functions
from datetime import datetime, timedelta
import asyncio
from googlesearch import search
from telethon.sessions import StringSession

api_id = 25850128
api_hash = 'a8ab96e84a1f76f6ff02460b15e36917'

client = TelegramClient('your_session', api_id, api_hash)
# Google qidiruv
@client.on(events.NewMessage(pattern=r'\.gog (.*)'))
async def google_search(event):
    search_term = event.pattern_match.group(1)
    await event.edit('Qidirilmoqda.....🔍')
    
    results = search(search_term, num_results=1)  # 5 ta natijani olish
    response = 'Google topilgan natija 🎟:\n'
    for result in results:
        response += f'{result}\n'
    
    # Xabarni tahrirlash
    await event.edit(response)

# AFK va Soat funksiyalari
is_afk = False
time_status = False

@client.on(events.NewMessage(pattern=r'\.help'))
async def help_handler(event):
    await event.edit('Assalomu aleykum 🥰\n\n▪️ Nicka soat: .soaton .soatoff\n\n▪️ AFK Rejim: .afkon / .afkoff \n\n▪️Golislar: .mu\n\n▪️Google bõlim: .gog')

@client.on(events.NewMessage(pattern=r'\.afkon'))
async def afk_on(event):
    global is_afk
    is_afk = True
    await event.edit("AFK rejim ornatildi!")

@client.on(events.NewMessage(pattern=r'\.afkoff'))
async def afk_off(event):
    global is_afk
    is_afk = False
    await event.edit("AFK rejim o'chirildi")
    

@client.on(events.NewMessage())
async def handle_afk_message(event):
    global is_afk
    if is_afk and not event.out:
        await event.respond("Uzr, hozircha AFK rejimdan ⛔️\nTez orada qaytib kelaman.\nBiror xabaringiz bõlsa yozing.\nRaxmat bro🗿")

async def update_profile_time():
    while time_status:
        now = datetime.now()
        time_str = now.strftime("| %H : %M")
        next_update = (now + timedelta(minutes=1)).replace(second=0, microsecond=0)
        delay = (next_update - now).total_seconds()

        try:
            if now.second == 0:
                new_time_str = time_str.replace(':', ' :')  # Replace with double-struck colon
                await client(functions.account.UpdateProfileRequest(about="Umir õtmoqda 🍃 " + new_time_str))
                await client(functions.account.UpdateProfileRequest(last_name=new_time_str))
        except Exception as e:
            print(f"Xatolik yuz berdi: {e}")

        await asyncio.sleep(delay)

@client.on(events.NewMessage(pattern=r'\.soaton'))
async def set_time_on(event):
    global time_status
    time_status = True
    asyncio.create_task(update_profile_time())
    await event.edit('<emoji document_id=5454415424319931791>⌚</emoji> <b>Nick va bio ga soat qõyildi</b>',parse_mode="HTML")

@client.on(events.NewMessage(pattern=r'\.soatoff'))
async def set_time_off(event):
    global time_status
    time_status = False
    await client(functions.account.UpdateProfileRequest(last_name=""))
    await client(functions.account.UpdateProfileRequest(about=""))
    await event.edit('<emoji document_id=5462928646501055704>🥲</emoji> <b>Nick va bio dagi soatlar ochirildi</b>', parse_mode="HTML")

# Ovozli memlar funksiyalari
class FakeMod:
    def __init__(self, client):
        self.client = client

    async def voicecmd(self, message):
        pass

@client.on(events.NewMessage(pattern=r'\.asalom', outgoing=True))
async def send_asalom_voice(event):
    fake_mod = FakeMod(client)
    await fake_mod.voicecmd(event.message)
    reply = await event.get_reply_message()
    await event.delete()
    await client.send_file(event.to_id, "https://t.me/Sruserbott/2", voice_note=True, reply_to=reply.id if reply else None)

@client.on(events.NewMessage(pattern=r'\.tugadi', outgoing=True))
async def send_tugadi_voice(event):
    fake_mod = FakeMod(client)
    await fake_mod.voicecmd(event.message)
    reply = await event.get_reply_message()
    await event.delete()
    await client.send_file(event.to_id, "https://t.me/Sruserbott/9", voice_note=True, reply_to=reply.id if reply else None)

@client.on(events.NewMessage(pattern=r'\.nimagp', outgoing=True))
async def send_nimagp_voice(event):
    fake_mod = FakeMod(client)
    await fake_mod.voicecmd(event.message)
    reply = await event.get_reply_message()
    await event.delete()
    await client.send_file(event.to_id, "https://t.me/Sruserbott/4", voice_note=True, reply_to=reply.id if reply else None)
    
async def voicecmd(self, message):
    activity_time = 5
    await message.delete()
    try:
        async with self.client.action(message.chat_id, "record-audio"):
            await asyncio.sleep(int(activity_time))
    except Exception as e:
        print(f"An error occurred: {e}")

@client.on(events.NewMessage(pattern=r'\.mu', outgoing=True))
async def voicemem(event):
    await event.edit("""<b><emoji document_id=5188377234380954537>🌘</emoji> Ovozli Memlar
<emoji document_id=5411174771620585784>😁</emoji> Voice Mems 🔊

<emoji document_id=5386350242901800909>▪</emoji> Voy blaa - <code>.voy blaa</code>

<emoji document_id=5386350242901800909>▪</emoji> Qotogdi yebsan shu gapinga Miyachanga pizdes pizdes ideyalar keb ketadiya qotog bilan ursada kalanga - <code>.q yebsan</code>

<emoji document_id=5386350242901800909>▪</emoji> Poxuy manga - <code>.px manga</code>

<emoji document_id=5386350242901800909>▪</emoji> Dunyo sharin tashkir etur... gandon mana shulardan biri  - <code>.gndn</code>

<emoji document_id=5386350242901800909>▪</emoji> Olga dalbayoblar biz dunyoni qolga olamiz dunyo bizniki boladi  - <code>.olga dlb</code>

<emoji document_id=5386350242901800909>▪</emoji> Junior bosh nima gap deyish kere  - <code>.junior bosh</code>

<emoji document_id=5386350242901800909>▪</emoji> nimagaaaaaap - <code>.nimagp</code>

<emoji document_id=5386350242901800909>▪</emoji> Hammasiga kulib qoydim takrorlayman hammasiga kulib qoydim  - <code>.k qoydim</code>

<emoji document_id=5386350242901800909>▪</emoji> Õ assalomu alekum bratm - <code>.asalom</code>

<emoji document_id=5386350242901800909>▪</emoji> tugadu - <code>.tugadi</code>

<emoji document_id=5386350242901800909>▪</emoji> Shu gapizga monovini va monovini va hammani asabin yebsiz - <code>.a yebsiz</code>

<emoji document_id=5386350242901800909>▪</emoji> Pashol naxuy men seni dadang manmi haromi - <code>.pnx haromi</code>

<emoji document_id=5386350242901800909>▪</emoji> deysan sen hozir chundingmi nima deganingni chundingmi san - <code>.nm deysan</code>

<emoji document_id=5386350242901800909>▪</emoji> Assalom aleykoom - <code>.asalo me
kom</code>
</b>""", parse_mode="HTML")

@client.on(events.NewMessage(pattern=r'\.voy blaa', outgoing=True))
async def blla(event):
    fake_mod = FakeMod(client)
    await fake_mod.voicecmd(event.message)
    reply = await event.get_reply_message()
    await event.delete()
    await event.client.send_file(event.to_id, "https://t.me/nxnxnxnxnxdnx/19", voice_note=True, reply_to=reply.id if reply else None)

@client.on(events.NewMessage(pattern=r'\.asalo mekom', outgoing=True))
async def asolo(event):
    fake_mod = FakeMod(client)
    await fake_mod.voicecmd(event.message)
    reply = await event.get_reply_message()
    await event.delete()
    await event.client.send_file(event.to_id, "https://t.me/nxnxnxnxnxdnx/7", voice_note=True, reply_to=reply.id if reply else None)

@client.on(events.NewMessage(pattern=r'\.nm deysan', outgoing=True))
async def nmdeysa(event):
    fake_mod = FakeMod(client)
    await fake_mod.voicecmd(event.message)
    reply = await event.get_reply_message()
    await event.delete()
    await event.client.send_file(event.to_id, "https://t.me/nxnxnxnxnxdnx/14", voice_note=True, reply_to=reply.id if reply else None)

@client.on(events.NewMessage(pattern=r'\.pnx haromi', outgoing=True))
async def pnxharomi(event):
    fake_mod = FakeMod(client)
    await fake_mod.voicecmd(event.message)
    reply = await event.get_reply_message()
    await event.delete()
    await event.client.send_file(event.to_id, "https://t.me/nxnxnxnxnxdnx/11", voice_note=True, reply_to=reply.id if reply else None)

@client.on(events.NewMessage(pattern=r'\.a yebsiz', outgoing=True))
async def asab(event):
    fake_mod = FakeMod(client)
    await fake_mod.voicecmd(event.message)
    reply = await event.get_reply_message()
    await event.delete()
    await event.client.send_file(event.to_id, "https://t.me/nxnxnxnxnxdnx/18", voice_note=True, reply_to=reply.id if reply else None)

@client.on(events.NewMessage(pattern=r'\.p kopayib', outgoing=True))
async def pulkopayib(event):
    fake_mod = FakeMod(client)
    await fake_mod.voicecmd(event.message)
    reply = await event.get_reply_message()
    await event.delete()
    await event.client.send_file(event.to_id, "https://t.me/nxnxnxnxnxdnx/21", voice_note=True, reply_to=reply.id if reply else None)

@client.on(events.NewMessage(pattern=r'\.k qoydim', outgoing=True))
async def kulib(event):
    fake_mod = FakeMod(client)
    await fake_mod.voicecmd(event.message)
    reply = await event.get_reply_message()
    await event.delete()
    await event.client.send_file(event.to_id, "https://t.me/nxnxnxnxnxdnx/12", voice_note=True, reply_to=reply.id if reply else None)

@client.on(events.NewMessage(pattern=r'\.junior bosh', outgoing=True))
async def junior(event):
    fake_mod = FakeMod(client)
    await fake_mod.voicecmd(event.message)
    reply = await event.get_reply_message()
    await event.delete()
    await event.client.send_file(event.to_id, "https://t.me/nxnxnxnxnxdnx/13", voice_note=True, reply_to=reply.id if reply else None)

@client.on(events.NewMessage(pattern=r'\.olga dlb', outgoing=True))
async def dlb(event):
    fake_mod = FakeMod(client)
    await fake_mod.voicecmd(event.message)
    reply = await event.get_reply_message()
    await event.delete()
    await event.client.send_file(event.to_id, "https://t.me/nxnxnxnxnxdnx/6", voice_note=True, reply_to=reply.id if reply else None)

@client.on(events.NewMessage(pattern=r'\.gndn', outgoing=True))
async def gndn(event):
    fake_mod = FakeMod(client)
    await fake_mod.voicecmd(event.message)
    reply = await event.get_reply_message()
    await event.delete()
    await event.client.send_file(event.to_id, "https://t.me/nxnxnxnxnxdnx/3", voice_note=True, reply_to=reply.id if reply else None)

@client.on(events.NewMessage(pattern=r'\.px manga', outgoing=True))
async def pxmanga(event):
    fake_mod = FakeMod(client)
    await fake_mod.voicecmd(event.message)
    reply = await event.get_reply_message()
    await event.delete()
    await event.client.send_file(event.to_id, "https://t.me/nxnxnxnxnxdnx/2", voice_note=True, reply_to=reply.id if reply else None)

@client.on(events.NewMessage(pattern=r'\.q yebsan', outgoing=True))
async def qyebsan(event):
    fake_mod = FakeMod(client)
    await fake_mod.voicecmd(event.message)
    reply = await event.get_reply_message()
    await event.delete()
    await event.client.send_file(event.to_id, "https://t.me/nxnxnxnxnxdnx/4", voice_note=True, reply_to=reply.id if reply else None)
    
# Klientni boshlash
client.start()
client.run_until_disconnected()
