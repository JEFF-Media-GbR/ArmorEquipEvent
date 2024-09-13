# ArmorEquipEvent
<!--- Buttons start -->
<p align="center">
  <a href="https://www.spigotmc.org/threads/arnuhs-armorequipevent.545188/">
    <img src="https://static.jeff-media.com/img/button_spigotmc_thread.png?3" alt="SpigotMC Thread">
  </a>
  <a href="https://hub.jeff-media.com/javadocs/com/jeff-media/armor-equip-event/1.0.2/">
    <img src="https://static.jeff-media.com/img/button_javadocs.png?3" alt="Javadocs">
  </a>
  <a href="https://discord.jeff-media.com/">
    <img src="https://static.jeff-media.com/img/button_discord.png?3" alt="Discord">
  </a>
  <a href="https://paypal.me/mfnalex">
    <img src="https://static.jeff-media.com/img/button_donate.png?3" alt="Donate">
  </a>
</p>
<!--- Buttons end -->
This is a maintained version of <a href="https://github.com/Arnuh/ArmorEquipEvent">Arnuh's ArmorEquipEvent</a> including some bug fixes and a proper maven artifact.

## Maven information

The latest version is available on Maven Central:

```xml
<dependency>
  <groupId>com.jeff-media</groupId>
  <artifactId>armor-equip-event</artifactId>
  <version>1.0.3</version>
  <scope>compile</scope>
</dependency>
```

Please note that you must also shade and relocate the artifact:

```xml
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-shade-plugin</artifactId>
      <version>3.5.0</version>
      <configuration>
        <relocations>
          <relocation>
            <pattern>com.jeff_media.armorequipevent</pattern>
            <shadedPattern>YOUR.PACKAGE.NAME.armorequipevent</shadedPattern>
          </relocation>
        </relocations>
      </configuration>
      <executions>
        <execution>
          <phase>package</phase>
          <goals>
            <goal>shade</goal>
          </goals>
        </execution>
      </executions>
    </plugin>
  </plugins>
</build>
```

## Usage

To use the ArmorEquipEvent, you first have to register the Listener, for example in your onEnable() method:

```java
import com.jeff_media.armorequipevent.ArmorEquipEvent;
import org.bukkit.plugin.java.JavaPlugin;

public class MyPlugin extends JavaPlugin {

    @Override
    public void onEnable() {
        ArmorEquipEvent.registerListener(this);
    }
    
}
```

You can now listen to this event, cancel it or change the equipped armor.

## Javadocs

Javadocs are available here: https://hub.jeff-media.com/javadocs/armorequipevent

## Changes

The following things have changed since the latest version of Arnuh's original ArmorEquipEvent:

- getNewArmorPiece() and getOldArmorPiece() properly return null instead of returning an empty itemstack sometimes
- The event properly gets called when equipping or unequipping armor using the hotbar swap key
- Prevents the event from being called when setting setKeepInventory in the PlayerDeathEvent to true (the original version only detects this on LOW and LOWEST priority)
- Available as a maven artifact - no need to copy/paste classes manually

## Other libraries by me

### [CustomBlockData](https://github.com/JEFF-Media-GbR/CustomBlockData)
My **CustomBlockData** library provides a PersistentDataContainer for every block in your world - easily save EVERY information you like inside blocks, without any external storage needed!

### [MorePersistentDataTypes](https://github.com/JEFF-Media-GbR/MorePersistentDataTypes)
Adds a ton of new **PersistentDataTypes** to use with Bukkit's PersistentDataContainer.

### [SpigotUpdateChecker](https://github.com/JEFF-Media-GbR/Spigot-UpdateChecker)
Powerful **UpdateChecker** for your plugins, with only **one line of code**.

## Discord

If you need help, feel free to join my Discord server and head to #programming-help:

<a href="https://discord.jeff-media.com"><img src="https://api.jeff-media.de/img/discord1.png"></a>

## Donate

If you are using this project in your paid plugins, or if you just want to buy me a coffee, I would be happy over a small donation :)

<a href="https://paypal.me/mfnalex"><img src="https://www.paypalobjects.com/en_US/DK/i/btn/btn_donateCC_LG.gif" border="0" name="submit" title="PayPal - The safer, easier way to pay online!" alt="Donate with PayPal" /></a>
