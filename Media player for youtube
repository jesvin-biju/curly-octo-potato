
from tkinter import *
from pytube import YouTube
import vlc  # Make sure to have the python-vlc library installed

root = Tk()
root.geometry('600x400')
root.resizable(0, 0)
root.title("YouTube Video Player & Downloader")

Label(root, text='YouTube Video Player & Downloader', font='arial 20 bold').pack()

link = StringVar()

Label(root, text='Paste Link Here:', font='arial 15 bold').place(x=200, y=60)
link_enter = Entry(root, width=70, textvariable=link).place(x=32, y=90)


def Downloader():
    url = YouTube(str(link.get()))
    video = url.streams.get_highest_resolution()
    video.download()
    Label(root, text='DOWNLOADED', font='arial 15').place(x=250, y=210)


Button(root, text='DOWNLOAD', font='arial 15 bold', bg='pale violet red', padx=2, command=Downloader).place(x=230, y=150)


# --- Media Player Section ---

# Initialize the media player
Instance = vlc.Instance()
player = Instance.media_player_new()
player.set_mrl('')

# Function to play the downloaded video
def Play():
    url = YouTube(str(link.get()))
    video = url.streams.get_highest_resolution()
    video.download()
    media = Instance.media_new(video.default_filename)
    player.set_media(media)
    player.play()

Button(root, text='PLAY', font='arial 15 bold', bg='light green', padx=2, command=Play).place(x=100, y=250)


# Function to pause the video
def Pause():
    player.pause()

Button(root, text='PAUSE', font='arial 15 bold', bg='yellow', padx=2, command=Pause).place(x=250, y=250)


# Function to forward the video by 10 seconds
def Forward():
    player.set_time(player.get_time() + 10000)  # 10000 milliseconds = 10 seconds

Button(root, text='FORWARD 10s', font='arial 15 bold', bg='orange', padx=2, command=Forward).place(x=380, y=250)


# Function to rewind the video by 10 seconds
def Rewind():
    player.set_time(player.get_time() - 10000)  # 10000 milliseconds = 10 seconds

Button(root, text='REWIND 10s', font='arial 15 bold', bg='light blue', padx=2, command=Rewind).place(x=100, y=300)

root.mainloop()
