-- carregar blibioteca
local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()

local Window = Fluent:CreateWindow({
    Title = "moizes777 hub" .. Fluent.Version,
    TabWidth = 160, Size = UDim2.fromOffset(580, 460), Theme = "Dark"
})

local Tabs = {
    Main = Window:AddTab({ Title = "Main" }),
    Settings = Window:AddTab({ Title = "Settings", Icon = "settings" })
}

-- parágrafos 
Tabs.Main:AddParagraph({ Title = "moizes777 script ", Content = "moizes777 script novo" })

-- botões 
Tabs.Main:AddButton({ Title = "infinite jump", Callback = function()

local InfiniteJumpEnabled = true

game:GetService("UserInputService").JumpRequest:connect(function()

	if InfiniteJumpEnabled then

		game:GetService"Players".LocalPlayer.Character:FindFirstChildOfClass'Humanoid':ChangeState("Jumping")

	end

end)

 end })

-- alterador

 local Toggle = Tabs.Main:AddToggle("autoFarm",

 {

     Title = "autofarm",

     Description = "ele vai Farma level",

     Default = false, -- "," e preciso coloque em qualquer 

     Callback = function(state)

     if state then

         Fluent:Notify({ Title = "autoFarm ligado", Content = "teste" })

     else

         Fluent:Notify({ Title = "desligando", Content = "desligado" })

         end

      end

})



-- slides
local Slider = Tabs.Main:AddSlider("pulo", {

        Title = "ajustar pulo ",

        Description = "irar mudar o pulo do jogador",

        Default = 2,

        Min = 0,

        Max = 5,

        Rounding = 1,

        Callback = function(Value)

            print("Slider was changed:", Value)

        end

    })



    Slider:OnChanged(function(Value)

        print("pulo mudou pra :", Value)

    end)

    
 -- slider de velocidade (WalkSpeed)

local WalkSlider = Tabs.Main:AddSlider("velocidade", {

    Title = "Ajustar Velocidade",

    Description = "Muda a velocidade do jogador",

    Default = 16, -- velocidade padrÃ£o do Roblox

    Min = 10,

    Max = 200,

    Rounding = 0,

    Callback = function(Value)

        local humanoid = game:GetService("Players").LocalPlayer.Character:FindFirstChildOfClass("Humanoid")

        if humanoid then

            humanoid.WalkSpeed = Value

        end

        print("WalkSpeed mudou para:", Value)

    end

})
WalkSlider:OnChanged(function(Value)

    print("Slider de velocidade atualizado para:", Value)

end)
