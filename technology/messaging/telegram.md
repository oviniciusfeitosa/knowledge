# Telegram

## ABNT2 keyboard layout

Open the file "/home/your\_user/.local/share/applications/telegramdesktop.desktop".

You will see something like this:

```text
[Desktop Entry]                                                                                                                                                         
 Version=1.0                                                                                                                                                             
 Name=Telegram Desktop                                                                                                                                                   
 Comment=Official desktop application for the Telegram messaging service                                                                                                 
 TryExec=/opt/telegram/telegram                                                                                                                                          
 Exec=/opt/telegram/telegram -- %u                                                                                                                                       
 Icon=telegram                                                                                                                                                           
 Terminal=false                                                                                                                                                          
 StartupWMClass=TelegramDesktop                                                                                                                                          
 Type=Application                                                                                                                                                        
 Categories=Network;InstantMessaging;Qt;                                                                                                                                 
 MimeType=x-scheme-handler/tg;                                                                                                                                           
 X-Desktop-File-Install-Version=0.23   
```

Change `Exec=/opt/telegram/telegram -- %u` to `Exec=env QT_IM_MODULE=xim /opt/telegram/telegram -- %u`  


