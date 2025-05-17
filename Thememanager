local httpService = game:GetService('HttpService')
local ThemeManager = {} do
	ThemeManager.Folder = 'LinoriaLibSettings'
	ThemeManager.Library = nil
ThemeManager.BuiltInThemes = {
    ['Default'] = { 1, httpService:JSONDecode('{"FontColor":"BFBFBF","MainColor":"0F0F0F","AccentColor":"9e00ff","BackgroundColor":"101010","OutlineColor":"0B0B0B"}') },
	['Rainbow'] = { 2, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"0F0F0F","AccentColor":"ff0000","BackgroundColor":"101010","OutlineColor":"0B0B0B"}') },
    ['Venom'] = { 3, httpService:JSONDecode('{"FontColor":"BFBFBF","MainColor":"0E0E0E","AccentColor":"ff0000","BackgroundColor":"0E0E0E","OutlineColor":"0B0B0B"}') },
    ['Cyan'] = { 4, httpService:JSONDecode('{"FontColor":"BFBFBF","MainColor":"0F0F0F","AccentColor":"00ffef","BackgroundColor":"101010","OutlineColor":"0B0B0B"}') },
    ['Burn'] = { 5, httpService:JSONDecode('{"FontColor":"FF8200","MainColor":"0C0C0C","AccentColor":"FF8200","BackgroundColor":"0C0C0C","OutlineColor":"0C0C0C"}') },
    ['Fatality'] = { 6, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"1e1842","AccentColor":"c50754","BackgroundColor":"191335","OutlineColor":"28204F"}') },
    ['GameSense'] = { 7, httpService:JSONDecode('{"FontColor":"FFFFFF","MainColor":"171717","AccentColor":"98E22E","BackgroundColor":"171717","OutlineColor":"31371C"}') },
    ['Comet.pub'] = { 8, httpService:JSONDecode('{"FontColor":"5E5E5E","MainColor":"0F0F0F","AccentColor":"5D589D","BackgroundColor":"0F0F0F","OutlineColor":"191919"}') },
    ['BBot'] = { 9, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"1e1e1e","AccentColor":"7e48a3","BackgroundColor":"232323","OutlineColor":"141414"}') },
    ['Jester'] = { 10, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"242424","AccentColor":"db4467","BackgroundColor":"1c1c1c","OutlineColor":"373737"}') },
    ['Mint'] = { 11, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"242424","AccentColor":"3db488","BackgroundColor":"1c1c1c","OutlineColor":"373737"}') },
    ['Tokyo Night'] = { 12, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"191925","AccentColor":"6759b3","BackgroundColor":"16161f","OutlineColor":"323232"}') },
    ['Ubuntu'] = { 13, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"3e3e3e","AccentColor":"e2581e","BackgroundColor":"323232","OutlineColor":"191919"}') },
    ['Quartz'] = { 14, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"232330","AccentColor":"426e87","BackgroundColor":"1d1b26","OutlineColor":"27232f"}') },
    ['Neon Blue'] = { 15, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"0A0A20","AccentColor":"1D73E8","BackgroundColor":"101030","OutlineColor":"232349"}') },
    ['Electric Purple'] = { 16, httpService:JSONDecode('{"FontColor":"F2F2F2","MainColor":"1A1A2E","AccentColor":"8B1AC0","BackgroundColor":"121227","OutlineColor":"2A1F52"}') },
    ['Sunset Orange'] = { 17, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"2B1F13","AccentColor":"FF5733","BackgroundColor":"1F1410","OutlineColor":"3B2523"}') },
    ['Forest Green'] = { 18, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"1B2A2F","AccentColor":"55C665","BackgroundColor":"142C3C","OutlineColor":"243B3F"}') },
    ['Midnight Gold'] = { 19, httpService:JSONDecode('{"FontColor":"D4D4D4","MainColor":"2E1D2D","AccentColor":"D1A100","BackgroundColor":"1F0F0F","OutlineColor":"2B1414"}') },
    ['Ocean Breeze'] = { 20, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"1F3A47","AccentColor":"58C1D4","BackgroundColor":"14292E","OutlineColor":"233B43"}') },
    ['Dark Cherry'] = { 21, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"2E0B0B","AccentColor":"B72A2A","BackgroundColor":"1F0707","OutlineColor":"381818"}') },
    ['Mystic Teal'] = { 22, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"172A2F","AccentColor":"006D66","BackgroundColor":"122C2A","OutlineColor":"2C4643"}') },
    ['Frostbite'] = { 23, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"2E3B3F","AccentColor":"A8D8E8","BackgroundColor":"192A2E","OutlineColor":"2A4C53"}') },
    ['Space Odyssey'] = { 24, httpService:JSONDecode('{"FontColor":"E4E4E4","MainColor":"121A26","AccentColor":"6E83B7","BackgroundColor":"0D1219","OutlineColor":"283346"}') },
    ['Cyberpunk Pink'] = { 25, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"2B0F25","AccentColor":"FF58A0","BackgroundColor":"1D0C1C","OutlineColor":"391E2A"}') },
    ['Vivid Green'] = { 26, httpService:JSONDecode('{"FontColor":"ffffff","MainColor":"263A23","AccentColor":"9CE1A3","BackgroundColor":"1F2F1C","OutlineColor":"2C3F28"}') }
}

	function ThemeManager:ApplyTheme(theme)
		local customThemeData = self:GetCustomTheme(theme)
		local data = customThemeData or self.BuiltInThemes[theme]

		if not data then return end

		local scheme = data[2]
		for idx, col in next, customThemeData or scheme do
			self.Library[idx] = Color3.fromHex(col)
			
			if Options[idx] then
				Options[idx]:SetValueRGB(Color3.fromHex(col))
			end
		end

		if theme == "Rainbow" then
			spawn(function()
				while Options.ThemeManager_ThemeList.Value == "Rainbow" do
					local hue = tick() % 5 / 5
					local color = Color3.fromHSV(hue, 1, 1)
					self.Library.AccentColor = color
					if Options.AccentColor then
						Options.AccentColor:SetValueRGB(color)
					end
					self:ThemeUpdate()
					task.wait(0.25)
				end
			end)
		end
		self:ThemeUpdate()
	end

	function ThemeManager:ThemeUpdate()
		local options = { "FontColor", "MainColor", "AccentColor", "BackgroundColor", "OutlineColor" }
		for i, field in next, options do
			if Options and Options[field] then
				self.Library[field] = Options[field].Value
			end
		end

		self.Library.AccentColorDark = self.Library:GetDarkerColor(self.Library.AccentColor);
		self.Library:UpdateColorsUsingRegistry()
	end

	function ThemeManager:LoadDefault()		
		local theme = 'Default'
		local content = isfile(self.Folder .. '/themes/default.txt') and readfile(self.Folder .. '/themes/default.txt')

		local isDefault = true
		if content then
			if self.BuiltInThemes[content] then
				theme = content
			elseif self:GetCustomTheme(content) then
				theme = content
				isDefault = false;
			end
		elseif self.BuiltInThemes[self.DefaultTheme] then
		 	theme = self.DefaultTheme
		end

		if isDefault then
			Options.ThemeManager_ThemeList:SetValue(theme)
		else
			self:ApplyTheme(theme)
		end
	end

	function ThemeManager:SaveDefault(theme)
		writefile(self.Folder .. '/themes/default.txt', theme)
	end

	function ThemeManager:CreateThemeManager(groupbox)
        groupbox:AddDivider()
		groupbox:AddLabel('Background color'):AddColorPicker('BackgroundColor', { Default = self.Library.BackgroundColor });
		groupbox:AddLabel('Main color')	:AddColorPicker('MainColor', { Default = self.Library.MainColor });
		groupbox:AddLabel('Accent color'):AddColorPicker('AccentColor', { Default = self.Library.AccentColor });
		groupbox:AddLabel('Outline color'):AddColorPicker('OutlineColor', { Default = self.Library.OutlineColor });
		groupbox:AddLabel('Font color')	:AddColorPicker('FontColor', { Default = self.Library.FontColor });

		local ThemesArray = {}
		for Name, Theme in next, self.BuiltInThemes do
			table.insert(ThemesArray, Name)
		end

		table.sort(ThemesArray, function(a, b) return self.BuiltInThemes[a][1] < self.BuiltInThemes[b][1] end)

		groupbox:AddDivider()
		groupbox:AddDropdown('ThemeManager_ThemeList', { Text = 'Theme list', Values = ThemesArray, Default = 1 })

		groupbox:AddButton('Set as default', function()
			self:SaveDefault(Options.ThemeManager_ThemeList.Value)
			self.Library:Notify(string.format('Set default theme to %q', Options.ThemeManager_ThemeList.Value))
		end)

		Options.ThemeManager_ThemeList:OnChanged(function()
			self:ApplyTheme(Options.ThemeManager_ThemeList.Value)
		end)

		groupbox:AddDivider()
		groupbox:AddDropdown('ThemeManager_CustomThemeList', { Text = 'Custom themes', Values = self:ReloadCustomThemes(), AllowNull = true, Default = 1 })
		groupbox:AddInput('ThemeManager_CustomThemeName', { Text = 'Custom theme name' })

		groupbox:AddButton('Load theme', function() 
			self:ApplyTheme(Options.ThemeManager_CustomThemeList.Value) 
		end):AddButton('Save theme', function() 
			self:SaveCustomTheme(Options.ThemeManager_CustomThemeName.Value)

			Options.ThemeManager_CustomThemeList.Values = self:ReloadCustomThemes()
			Options.ThemeManager_CustomThemeList:SetValues()
			Options.ThemeManager_CustomThemeList:SetValue(nil)
		end)

		groupbox:AddButton('Refresh list', function()
			Options.ThemeManager_CustomThemeList.Values = self:ReloadCustomThemes()
			Options.ThemeManager_CustomThemeList:SetValues()
			Options.ThemeManager_CustomThemeList:SetValue(nil)
		end)

		groupbox:AddButton('Set as default', function()
			if Options.ThemeManager_CustomThemeList.Value ~= nil and Options.ThemeManager_CustomThemeList.Value ~= '' then
				self:SaveDefault(Options.ThemeManager_CustomThemeList.Value)
				self.Library:Notify(string.format('Set default theme to %q', Options.ThemeManager_CustomThemeList.Value))
			end
		end)

		ThemeManager:LoadDefault()

		local function UpdateTheme()
			self:ThemeUpdate()
		end

		Options.BackgroundColor:OnChanged(UpdateTheme)
		Options.MainColor:OnChanged(UpdateTheme)
		Options.AccentColor:OnChanged(UpdateTheme)
		Options.OutlineColor:OnChanged(UpdateTheme)
		Options.FontColor:OnChanged(UpdateTheme)
	end

	function ThemeManager:GetCustomTheme(file)
		local path = self.Folder .. '/themes/' .. file
		if not isfile(path) then
			return nil
		end

		local data = readfile(path)
		local success, decoded = pcall(httpService.JSONDecode, httpService, data)
		
		if not success then
			return nil
		end

		return decoded
	end

	function ThemeManager:SaveCustomTheme(file)
		if file:gsub(' ', '') == '' then
			return self.Library:Notify('Invalid file name for theme (empty)', 3)
		end

		local theme = {}
		local fields = { "FontColor", "MainColor", "AccentColor", "BackgroundColor", "OutlineColor" }

		for _, field in next, fields do
			theme[field] = Options[field].Value:ToHex()
		end

		writefile(self.Folder .. '/themes/' .. file .. '.json', httpService:JSONEncode(theme))
	end

	function ThemeManager:ReloadCustomThemes()
		local list = listfiles(self.Folder .. '/themes')

		local out = {}
		for i = 1, #list do
			local file = list[i]
			if file:sub(-5) == '.json' then
				-- i hate this but it has to be done ...

				local pos = file:find('.json', 1, true)
				local char = file:sub(pos, pos)

				while char ~= '/' and char ~= '\\' and char ~= '' do
					pos = pos - 1
					char = file:sub(pos, pos)
				end

				if char == '/' or char == '\\' then
					table.insert(out, file:sub(pos + 1))
				end
			end
		end

		return out
	end

	function ThemeManager:SetLibrary(lib)
		self.Library = lib
	end

	function ThemeManager:BuildFolderTree()
		local paths = {}

		-- build the entire tree if a path is like some-hub/phantom-forces
		-- makefolder builds the entire tree on Synapse X but not other exploits

		local parts = self.Folder:split('/')
		for idx = 1, #parts do
			paths[#paths + 1] = table.concat(parts, '/', 1, idx)
		end

		table.insert(paths, self.Folder .. '/themes')
		table.insert(paths, self.Folder .. '/settings')

		for i = 1, #paths do
			local str = paths[i]
			if not isfolder(str) then
				makefolder(str)
			end
		end
	end

	function ThemeManager:SetFolder(folder)
		self.Folder = folder
		self:BuildFolderTree()
	end

	function ThemeManager:CreateGroupBox(tab)
		assert(self.Library, 'Must set ThemeManager.Library first!')
		return tab:AddLeftGroupbox('Themes')
	end

	function ThemeManager:ApplyToTab(tab)
		assert(self.Library, 'Must set ThemeManager.Library first!')
		local groupbox = self:CreateGroupBox(tab)
		self:CreateThemeManager(groupbox)
	end

	function ThemeManager:ApplyToGroupbox(groupbox)
		assert(self.Library, 'Must set ThemeManager.Library first!')
		self:CreateThemeManager(groupbox)
	end

	ThemeManager:BuildFolderTree()
end
return ThemeManager
