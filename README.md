# tdbot lua library
the lua library for tdbot 1.6.6

# use tdbot.lua lua library 
> for use tdbot lua library you shoude required in source file
```
local tdbot = require "tdbot"
```
# get new update from telegram
```
# new message
{}
# inline query
{}
# result query
{}
# callback data
{}
```
# base source code
> for handel update you shoude 
```
local tdbot = require "tdbot"
local Bot = 1234567890
local SUDO = {
  ["143702561"] = "M.MehdiAnsari"
}

function tdbot_update_callback (update) 
   local msg = update.message
   if not msg.date then
      print(">> INVALID MEESAGE <<")
      return false
   elseif msg.date < os.time() - 60 then
      print(">>OLD MESSAGE<<")
      return false
   elseif msg.sender_user_id == Bot then
      print("BASE: GET SELF MESSAGE")
      return false
   end
   if msg.content["@type"] == "messageText" and SUDO[msg.sender_user_id] then
      local matches = {}
      for k,v in pairs({"^(.*)$","^(.*) (.*)$","^(.*) (.*) (.*)$","^(.*) (.*) (.*) (.*)$"}) do
          if string.match(text,v) then
             matches = { string.match(text,v) } 
          end
       end
       if matches[1]:lower() == "ping" or matches[1] == "ربات" then
          return tdbot.sendText(msg.chat_id,msg.id,"PONG!","md")
       end
   end
end
```
# Translations
persian
