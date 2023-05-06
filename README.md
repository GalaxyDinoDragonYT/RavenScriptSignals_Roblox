# Raven Script Signals
[Get it on Roblox](https://www.roblox.com/library/13362367568/RavenScriptSignals)

## Table of Contents
  + Module Functions And Classes
  + Code Samples

---

## Module Functions And Classes
  This section contains lists of functions found in the module and what they do. I know they shouldn't really be called classes but it's the closest I could get so. 
  
  Opt = optional argument
  Req = required argument
  
  #### RavenScriptSignals
    + The module when required
  
  #### Emitter
    + A new emitter, created with RavenScriptSignals.newEmitter()
  
  #### Listener
    + A new listener, created with #Emitter:Connect()
  
  #### RavenScriptSignals.newEmitter(<Emitter Settings (Opt)>)
    + Creates a new #Emitter

  #### RavenScriptSignals.emitterSettings
    + A table which represents the emitter settings. Should be used when giving settings for RavenScriptSignals.newEmitter()
    + Default is to allow both client and server side connections.
    
  #### RavenScriptSignals.connectToEmitter(<Emitter Id (Req)>, <Code (Req)>)
    + Emitter Id is the Id of the emitter you wish to connect to. This is obtained by #Emitter.id
    + Code is a function that runs when the #Emitter sends a signal. Any arguments sent by the #Emitter will be included
    + Used to connect to an #Emitter from Id.
  
  #### RavenScriptSignals.connectOnCreation(<Code (Req)>)
    + Server side only.
    + Creates a #Listener that listens for new #Emitter creations
    + The created #Emitter is passed as the first argument in the function.
    + Code is the function to be run on #Emitter creation
   
  #### RavenScriptSignals.readMe()
    + A function that outputs information about the module via print statments.
   
  #### Emitter:Emit(<Arguments (Opt)>)
    + Emits a signal to all connected listeners, will send any arguments given.
    
  #### Emitter:Destroy()
    + Destrpys the #Emitter.
  
  #### Emitter:Disconnect(<Listener Id (Req)>)
    + Disconnects a #Listener by Id.
    
  #### Emitter:Connect(<Code (Req)>)
    + Creates a new #Listener connected to the #Emitter. Code is the function run when a signal is emitted.

  #### Emitter.id
    + Id of the #Emitter
  
  #### Emitter.listeners
    + Table of connected #Listeners.
    
  #### Emitter.settings
    + Settings of the #Emitter.
    
  #### Listener:Disconnect()
    + Disconnects the #Listener from the #Emitter it's connected to.
  
  #### Listener.id
    + The Id of the #Listener.
  
  #### Listener.emitterId
    + The Id of the #Emitter it's connected to.
  
  #### Listener.code
    + The function that runs when a signal is reccived.
    
 ---
    
  ## Code Samples
  
  #### Simple single script emitter system
  ```lua
local ravenScriptSignals = require(13361629938) --Require the module

local newSettings = ravenScriptSignals.emitterSettings --Create a new emitter settings table
newSettings.serverSide = true --Can the signal be connected server side. Default is true
newSettings.clientSide = true --Can the signal be connected client side. Default is true

local emitter = ravenScriptSignals.newEmitter() --Create a new emitter

local connection = emitter:Connect(function(...) --Create a new connection to the emitter
	print(...) --Print out any variables sent
end)

emitter:Emit(1) --Emit a signal, sending number 1 as a variable

connection:Disconnect() --Disconnect the connection

emitter:Emit(2) --Emit another signal, this one isn't reccived by the connection above

print(ravenScriptSignals.getEmitters()) --Print a table of all the emitters

emitter:Destroy() --Destroy the emitter

print(ravenScriptSignals.getEmitters()) --Print a table of all the emitters again
```
  #### Example signal manager module script
```lua
local ravenScriptSignals = require(13361629938)

--[[

Code to manager signals goes here.

For example you could:
	-Make a series of emitters when the game loads.
	-Connect to all signals as they are made.

]]

return ravenScriptSignals
```

Any suggestions or bugs, create an issue. 
