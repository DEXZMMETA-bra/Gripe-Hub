-- [[ GRIPE HUB - BLOX FRUITS SCRIPT ]] --
-- Ícone da UI: 🍇 (Uva)
-- Estilo: W-Azure Inspirado

local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
   Name = "🍇 Gripe Hub | Leviathan Update",
   LoadingTitle = "Carregando Gripe Hub...",
   LoadingSubtitle = "by Developer",
   ConfigurationSaving = {
      Enabled = true,
      FolderName = "GripeHubConfig",
      FileName = "BloxFruits"
   }
})

-- =================================================================
-- TAB 1: Configuração de Skills (Skills Config)
-- =================================================================
local SkillsTab = Window:CreateTab("Configuração de Skills", 4483362458) -- Ícone genérico

-- Variáveis de Controle de Skills e Tempos (Cooldowns)
_G.Melee_Z = true; _G.Melee_X = true; _G.Melee_C = true; _G.Melee_CD = 0.5
_G.Sword_Z = true; _G.Sword_X = true; _G.Sword_CD = 0.5
_G.Fruit_Z = true; _G.Fruit_X = true; _G.Fruit_C = true; _G.Fruit_V = true; _G.Fruit_F = true; _G.Fruit_CD = 0.5
_G.Gun_Z = true; _G.Gun_X = true; _G.Gun_CD = 0.5

SkillsTab:CreateSection("Estilo de Luta (Melee) - Z, X, C")
SkillsTab:CreateToggle({
   Name = "Usar Skills de Melee",
   CurrentValue = true,
   Callback = function(Value) _G.UseMeleeSkills = Value end,
})

SkillsTab:CreateSection("Espada (Sword) - Z, X")
SkillsTab:CreateToggle({
   Name = "Usar Skills de Espada",
   CurrentValue = true,
   Callback = function(Value) _G.UseSwordSkills = Value end,
})

SkillsTab:CreateSection("Fruta (Blox Fruit) - Z, X, C, V, F")
SkillsTab:CreateToggle({
   Name = "Usar Skills de Fruta",
   CurrentValue = true,
   Callback = function(Value) _G.UseFruitSkills = Value end,
})

SkillsTab:CreateSection("Arma (Gun) - Z, X")
SkillsTab:CreateToggle({
   Name = "Usar Skills de Arma",
   CurrentValue = false,
   Callback = function(Value) _G.UseGunSkills = Value end,
})


-- =================================================================
-- TAB 2: Auto Leviathan (Foco Principal)
-- =================================================================
local LeviathanTab = Window:CreateTab("Auto Leviathan", 4483362458)

LeviathanTab:CreateToggle({
   Name = "Auto Encontrar Leviatã (Procurar no Mar)",
   CurrentValue = false,
   Callback = function(Value)
      _G.FindLeviathan = Value
      if Value then spawn(function() autoFindLeviathan() end) end
   end,
})

LeviathanTab:CreateToggle({
   Name = "Auto Atacar Leviatã & Segmentos",
   CurrentValue = false,
   Callback = function(Value)
      _G.KillLeviathan = Value
      if Value then spawn(function() autoAttackLeviathan() end) end
   end,
})

LeviathanTab:CreateToggle({
   Name = "Super Clique Rápido (T-Rex/Kitsune/Dragon)",
   CurrentValue = false,
   Callback = function(Value)
      _G.InstaClick = Value
      if Value then spawn(function() fastClickLoop() end) end
   end,
})

LeviathanTab:CreateSection("Barco & Utilidades do Mar")

LeviathanTab:CreateButton({
   Name = "Teleport: Ilha Congelada (Spy NPC)",
   Callback = function()
      -- Cód. Teleport para a Frozen Island
      game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-21000, 20, -15000) -- Coordenadas fictícias do mar
   end,
})

LeviathanTab:CreateToggle({
   Name = "Invocador de Barco Fantasma (Fake Player)",
   CurrentValue = false,
   Callback = function(Value)
      _G.SpawnFakeBoat = Value
      -- Lógica para simular a compra e trazer o barco até você
   end,
})

LeviathanTab:CreateToggle({
   Name = "Auto Lançar Arpão no Coração (Auto Fire Shot)",
   CurrentValue = false,
   Callback = function(Value) _G.AutoHarpoon = Value end,
})

LeviathanTab:CreateToggle({
   Name = "Barco Voador / Velocidade Máxima",
   CurrentValue = false,
   Callback = function(Value) _G.FlyBoat = Value end,
})

-- =================================================================
-- TAB 3: Outros Teleports e Práticas
-- =================================================================
local TeleportTab = Window:CreateTab("Teleports & Treino", 4483362458)

TeleportTab:CreateButton({
   Name = "Auto ir para Hydra Island",
   Callback = function()
      -- Cód. Teleport para Hydra Island
   end,
})

TeleportTab:CreateToggle({
   Name = "Praticar Sozinho (Desviar/Treinar Pulsação)",
   CurrentValue = false,
   Callback = function(Value) _G.AutoPractice = Value end,
})
