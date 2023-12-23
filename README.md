# WT32_ETH1 + MONGOOSE => Web-Server 

I used this 2 examples and merged them into one:  
ethernet-part: esp-idf\examples\ethernet\basic  
http-server-part: mongoose-master\examples\esp32\device-dashboard
  
Important setting is in the sdkconfig (created by menuconfig) - this must be set for ws32_eth1 -> and its different :P  
Internal EMAC: true  
RMII clock mode: external  
Ethernet PHY device: LAN87xx  
smi mdc: 23  
smi mdio: 18  
PHY reset: 16  
PHY addr: 1  

Here are the corresponding settings in the sdk config:  
...  
--Example Ethernet Configuration  
CONFIG_ENV_GPIO_RANGE_MIN=0  
CONFIG_ENV_GPIO_RANGE_MAX=39  
CONFIG_ENV_GPIO_IN_RANGE_MAX=39  
CONFIG_ENV_GPIO_OUT_RANGE_MAX=33   
CONFIG_EXAMPLE_USE_INTERNAL_ETHERNET=y  
CONFIG_EXAMPLE_ETH_PHY_LAN87XX=y  
CONFIG_EXAMPLE_ETH_MDC_GPIO=23  
CONFIG_EXAMPLE_ETH_MDIO_GPIO=18  
CONFIG_EXAMPLE_ETH_PHY_RST_GPIO=16  
CONFIG_EXAMPLE_ETH_PHY_ADDR=1  
--end of Example Ethernet Configuration  
...  
...  
--Ethernet  
CONFIG_ETH_ENABLED=y  
CONFIG_ETH_USE_ESP32_EMAC=y  
CONFIG_ETH_PHY_INTERFACE_RMII=y  
CONFIG_ETH_RMII_CLK_INPUT=y  
CONFIG_ETH_RMII_CLK_IN_GPIO=0  
CONFIG_ETH_DMA_BUFFER_SIZE=512  
CONFIG_ETH_DMA_RX_BUFFER_NUM=10  
CONFIG_ETH_DMA_TX_BUFFER_NUM=10  
--end of Ethernet
  
Biggest thanks go to Sergio R. Caprile @https://github.com/scaprile - without your kind help, i wouldnt have come so far :)
