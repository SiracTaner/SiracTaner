- 👋 Hi, I’m @SiracTaner
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
SiracTaner/SiracTaner is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
name: SmallAreaBuilder
version: 1.0
main: com.example.smallareabuilder.SmallAreaBuilder
api-version: 1.16
description: A plugin that generates a small 16x16 area of stone blocks.package com.example.smallareabuilder;

import org.bukkit.Bukkit;
import org.bukkit.Material;
import org.bukkit.World;
import org.bukkit.plugin.java.JavaPlugin;
import org.bukkit.Location;
import org.bukkit.block.Block;

public class SmallAreaBuilder extends JavaPlugin {

    @Override
    public void onEnable() {
        // Plugin etkinleştirildiğinde bu metot çalışır
        getLogger().info("SmallAreaBuilder eklentisi etkinleştirildi!");

        // Dünyayı alıyoruz
        World world = Bukkit.getWorld("world"); // Ana dünya adı genelde "world" olur.

        if (world != null) {
            // 16x16'lık taş platformu belirli bir koordinatta oluştur
            buildPlatform(world, 100, 64, 100);
        } else {
            getLogger().severe("Dünya bulunamadı!");
        }
    }

    public void buildPlatform(World world, int x, int y, int z) {
        // 16x16 taş platformu oluşturuyoruz
        for (int i = 0; i < 16; i++) {
            for (int j = 0; j < 16; j++) {
                Block block = world.getBlockAt(x + i, y, z + j);
                block.setType(Material.STONE); // Taş blok koyuyoruz
            }
        }
        getLogger().info("16x16'lık platform başarıyla oluşturuldu!");
    }

    @Override
    public void onDisable() {
        // Plugin devre dışı bırakıldığında bu metot çalışır
        getLogger().info("SmallAreaBuilder eklentisi devre dışı bırakıldı.");
    }
}
