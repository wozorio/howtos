# Configurar DNS IPv6 da CloudFlare no Roteador Arris da Claro

Existe um bug na interface gráfica do roteador que não permite configurar endereços IPv6 de servidores de DNS que não estejam dentro do range de IPv6 da Claro. Para contornar este problema, siga os passos abaixo.

## Configurando o roteador

1. Abra o navegador (ex: Google Chrome) e navegue até a página LAN IPv6 Settings
1. Pressione F12 para abrir o modo Developer Tools
1. Copie e cole o script abaixo na aba Console e pressione Enter

    ```javascript
    /*
    DISCLAIMER

    Do this at your own risk, as pretty much anything I post here! I'm not
    responsible if shit goes sideways and you need to reset the modem, call
    your ISP to fix it or move out of the country because someone decided to
    hunt you down. It should work though :)
    */

    validateIpv6 = () => true;
    arLanGatewayIp2.original_set = arLanGatewayIp2.set;
    arLanGatewayIp2.set = function (index, value, label, forceSubmit) {
    if (label == "IPAddressV6") { return; }
    arLanGatewayIp2.original_set.call(this, index, value, label, forceSubmit);
    };
    ```

1. Entre com os endereços IPv6 de DNS primário e secundário no campo DNS Override e pressione o botão Apply
