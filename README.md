UHCCore
=======
package me.Willraasch.BlocktoTnt;

import org.bukkit.Material;
import org.bukkit.block.Block;
import org.bukkit.command.defaults.TeleportCommand;
import org.bukkit.entity.Entity;
import org.bukkit.entity.Player;
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;
import org.bukkit.event.block.Action;
import org.bukkit.event.block.BlockPlaceEvent;
import org.bukkit.event.player.PlayerInteractEvent;
import org.bukkit.material.SpawnEgg;
import org.bukkit.plugin.java.JavaPlugin;

public class Core extends JavaPlugin implements Listener {

	@Override
	public void onEnable(){
		getServer().getPluginManager().registerEvents(this,this);
	}
    @Override
    public void onDisable(){
    	
    }
    
    @EventHandler
    public void onPlace(BlockPlaceEvent event){
    	Player player = event.getPlayer();
    	Block block = event.getBlock();
    	if (!player.isOp() && block.getType()==Material.TNT){
    		event.setCancelled(true);
    	}
    }
    
    @EventHandler
    public void onInteract(PlayerInteractEvent event){
    	Player player = event.getPlayer();
    	if (event.getAction()==Action.RIGHT_CLICK_BLOCK){
    		Block block = event.getClickedBlock();
    		if (player.isSneaking()){
    			block.setType(Material.TNT);
    			player.sendMessage("Run Nigga");
    			
    		}
    	}
    }
    
    
    
    
}
