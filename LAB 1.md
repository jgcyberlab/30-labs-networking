# LAB 1

Cenário
Uma pequena empresa possui um switch Cisco Catalyst e três setores (Administração, Vendas e TI)
que precisam ser isolados logicamente na mesma sala, sem uso de roteador.

Tarefas
1 Crie 3 VLANs: 10 (ADM), 20 (VENDAS), 30 (TI), com nomes descritivos.
2 Atribua as portas de acesso do switch às respectivas VLANs.
3 Teste conectividade entre hosts da mesma VLAN e confirme isolamento entre VLANs diferentes.
4 Documente a tabela de VLANs com 'show vlan brief'

Topologia:

!\[LabPics\\LAB1-1.png](./LabPics/LAB1-1.png)

É uma topologia simples, destinada à fundamentação de dispositivos, conectividade e segmentação lógica de redes.

Os PCs PC0 e PC1, PC2 e PC3, PC4 e PC5 estão conectados, respectivamente, às interfaces do Switch Cisco Catalyst 2960 configuradas com as VLANs 10, 20 e 30 (Administrativo, Vendas e TI).

Abaixo, segue a configuração das VLANs presente no Switch:

```jsx

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/7, Fa0/8, Fa0/9, Fa0/10
                                                Fa0/11, Fa0/12, Fa0/13, Fa0/14
                                                Fa0/15, Fa0/16, Fa0/17, Fa0/18
                                                Fa0/19, Fa0/20, Fa0/21, Fa0/22
                                                Fa0/23, Fa0/24, Gig0/1, Gig0/2
10   ADMINISTRATIVO                   active    Fa0/1, Fa0/2
20   VENDAS                           active    Fa0/3, Fa0/4
30   TI                               active    Fa0/5, Fa0/6
1002 fddi-default                     active    
1003 token-ring-default               active    
1004 fddinet-default                  active    
1005 trnet-default                    active    
```

OBS.: Não foi preciso configurar uma por vez, visto que utilizei o comando `interface range` .

Podemos reparar também que as VLANs não se comunicam entre si, já que não há mecanismo de roteamento.

Segue abaixo um teste do PC0 (192.168.10.2, parte da VLAN 10) tentando pingar o PC1 (192.168.10.3, também parte da VLAN 10) e sendo bem-sucedido.

!\[image.png](./LabPics/LAB1-2.png)

Por outro lado, o mesmo PC (PC0) não consegue pingar o PC2 (192.168.20.2) e nem o PC4(192.168.30.2), que fazem parte das VLANs 20 e 30, respectivamente.

!\[image.png](./LabPics/LAB1-3.png)

!\[image.png](./LabPics/LAB1-4.png)

Com isso, é possível ter uma visão prática de como funciona a segmentação lógica de uma LAN. Ainda não existe mecanismo de roteamento, mas também podemos fazer com que VLANs se comuniquem entre si.

Comandos utilizados:

`en` (enable)

`conf t` (configure terminal)

`interface range fa0/n-m` (`n` e `m` sendo as interfaces dentro do range)

`switchport mode access`

`switchport access vlan xx` (fazer a interface acessar a vlan designada)

`no shutdown`

