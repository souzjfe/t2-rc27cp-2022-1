# Scripts para Configuração da Topologia

## Coronel Vivida

1. Switch

   ```bash
   enable
   conf t
   hostname sw-filial2-js
   ip default-gateway 200.200.60.97
   interface vlan1
   description Filial2
   ip address 200.200.60.98 255.255.255.224
   no shutdown
   exit
   exit
   w
   ```

2. Roteador

   ```bash
   enable
   conf t
   hostname r-cv-js
   ipv6 unicast-routing
   interface fa0/0
   description Filial2
   ip address 200.200.60.97 255.255.255.224
   ipv6 address 2001:DB8:ACAD:3C02::1/64
   ipv6 enable
   no shutdown
   exit
   interface fa0/1
   description cv-ita
   ip address 200.200.60.242 255.255.255.252
   ipv6 address 2001:DB8:ACAD:3CFF::4:2/112
   ipv6 enable
   no shutdown
   exit
   ip route 200.200.60.0 255.255.255.192 200.200.60.241
   ip route 200.200.60.64 255.255.255.224 200.200.60.241
   ip route 200.200.60.224 255.255.255.252 200.200.60.241
   ip route 200.200.60.228 255.255.255.252 200.200.60.241
   ip route 200.200.60.232 255.255.255.252 200.200.60.241
   ip route 200.200.60.236 255.255.255.252 200.200.60.241
   ipv6 route 2001:DB8:ACAD:3C00::/64 2001:DB8:ACAD:3CFF::4:1
   ipv6 route 2001:DB8:ACAD:3C01::/64 2001:DB8:ACAD:3CFF::4:1
   ipv6 route 2001:DB8:ACAD:3CFF::/112 2001:DB8:ACAD:3CFF::4:1
   ipv6 route 2001:DB8:ACAD:3CFF::1:0/112 2001:DB8:ACAD:3CFF::4:1
   ipv6 route 2001:DB8:ACAD:3CFF::2:0/112 2001:DB8:ACAD:3CFF::4:1
   ipv6 route 2001:DB8:ACAD:3CFF::3:0/112 2001:DB8:ACAD:3CFF::4:1

   security passwords min-length 10
   login block-for 120 attempts 3 within 60
   line vty 0 15
   exec-timeout 5
   login local
   transport input ssh
   exit
   service password-encryption
   line con 0
   exec-timeout 5
   password @Cons-jeferson
   login
   exit
   enable secret @dmin-jeferson
   banner motd $	----------------------------------------------------------------
   | 															                                             |
   | Roteador Coronel Vivida			  			                                       |
   | 															                                             |
   | ATENCAO Acesso Restrito a pessoas autorizadas! 				                     |
   | 															                                             |
   | Administrador: JEFERSON ROSA DE SOUZA (jefsou@alunos.utfpr.edu.br) 	       |
   | 															                                             |
   -----------------------------------------------------------------------------$
   ip domain name jeferson.souza.com.br
   crypto key generate rsa general-keys modulus 1024
   username jeferson secret ssh@Network1ng
   exit
   w
   ```

## Francisco Beltrão

1. Switch

   ```bash
   enable
   conf t
   hostname sw-filial1-js
   ip default-gateway 200.200.60.65
   interface vlan1
   description Filial1
   ip address 200.200.60.66 255.255.255.224
   no shutdown
   exit
   exit
   w
   ```

2. Roteador

   ```bash
   enable
   conf t
   hostname r-fb-js
   ipv6 unicast-routing
   interface Se0/0/0
   description fb-ita
   clock rate 56000
   ip address 200.200.60.233 255.255.255.252
   ipv6 address 2001:DB8:ACAD:3CFF::2:1/112
   ipv6 enable
   no shutdown
   exit
   interface Se0/0/1
   description vit-fb
   ip address 200.200.60.230 255.255.255.252
   ipv6 address 2001:DB8:ACAD:3CFF::1:2/112
   ipv6 enable
   no shutdown
   exit
   interface fa0/0
   description Filial1
   ip address 200.200.60.65 255.255.255.224
   ipv6 address 2001:DB8:ACAD:3C01::1/64
   ipv6 address Fe80::1 link-local
   ipv6 enable
   no shutdown
   exit
   ip route 200.200.60.0 255.255.255.192 200.200.60.234
   ip route 200.200.60.96 255.255.255.224 200.200.60.234
   ip route 200.200.60.224 255.255.255.252 200.200.60.234
   ip route 200.200.60.236 255.255.255.252 200.200.60.234
   ip route 200.200.60.240 255.255.255.252 200.200.60.234
   ipv6 route 2001:DB8:ACAD:3C00::/64 2001:DB8:ACAD:3CFF::2:2
   ipv6 route 2001:DB8:ACAD:3C02::/64 2001:DB8:ACAD:3CFF::2:2
   ipv6 route 2001:DB8:ACAD:3CFF::3:0/112 2001:DB8:ACAD:3CFF::2:2
   ipv6 route 2001:DB8:ACAD:3CFF::/112 2001:DB8:ACAD:3CFF::2:2
   ipv6 route 2001:DB8:ACAD:3CFF::4:0/112 2001:DB8:ACAD:3CFF::2:2

   security passwords min-length 10
   login block-for 120 attempts 3 within 60
   line vty 0 15
   exec-timeout 5
   login local
   transport input ssh
   exit
   service password-encryption
   line con 0
   exec-timeout 5
   password @Cons-jeferson
   login
   exit
   enable secret @dmin-jeferson
   banner motd $	----------------------------------------------------------------
   | 															                                             |
   | Roteador Francisco Beltrão			  			                                   |
   | 															                                             |
   | ATENCAO Acesso Restrito a pessoas autorizadas! 				                     |
   | 															                                             |
   | Administrador: JEFERSON ROSA DE SOUZA (jefsou@alunos.utfpr.edu.br) 	       |
   | 															                                             |
   -----------------------------------------------------------------------------$
   ip domain name jeferson.souza.com.br
   crypto key generate rsa general-keys modulus 1024
   username jeferson secret ssh@Network1ng
   exit
   w
   ```

## Pato Branco

1. Switch

   ```bash
   enable
   conf t
   hostname sw-matriz-js
   ip default-gateway 200.200.60.1
   interface vlan1
   description Matriz
   ip address 200.200.60.2 255.255.255.192
   no shutdown
   exit
   exit
   w
   ```

2. Roteador

   ```bash
   enable
   conf t
   hostname r-pb-js
   ipv6 unicast-routing
   interface Se0/0/0
   description pb-vit
   clock rate 56000
   ip address 200.200.60.225 255.255.255.252
   ipv6 address 2001:DB8:ACAD:3CFF::1/112
   ipv6 enable
   no shutdown
   exit
   interface Se0/0/1
   description ita-pb
   ip address 200.200.60.238 255.255.255.252
   ipv6 address 2001:DB8:ACAD:3CFF::3:2/112
   ipv6 enable
   no shutdown
   exit
   interface fa0/0
   description Matriz
   ip address 200.200.60.1 255.255.255.192
   ipv6 address 2001:DB8:ACAD:3C00::1/64
   ipv6 address Fe80::1 link-local
   ipv6 enable
   no shutdown
   exit
   ip route 200.200.60.228 255.255.255.252 200.200.60.226
   ip route 200.200.60.232 255.255.255.252 200.200.60.226
   ip route 200.200.60.240 255.255.255.252 200.200.60.226
   ip route 200.200.60.64 255.255.255.224 200.200.60.226
   ip route 200.200.60.96 255.255.255.224 200.200.60.226
   ipv6 route 2001:DB8:ACAD:3CFF::1:0/112 2001:DB8:ACAD:3CFF::2
   ipv6 route 2001:DB8:ACAD:3CFF::2:0/112 2001:DB8:ACAD:3CFF::2
   ipv6 route 2001:DB8:ACAD:3CFF::4:0/112 2001:DB8:ACAD:3CFF::2
   ipv6 route 2001:DB8:ACAD:3C01::/64 2001:DB8:ACAD:3CFF::2
   ipv6 route 2001:DB8:ACAD:3C02::/64 2001:DB8:ACAD:3CFF::2

   security passwords min-length 10
   login block-for 120 attempts 3 within 60
   line vty 0 15
   exec-timeout 5
   login local
   transport input ssh
   exit
   service password-encryption
   line con 0
   exec-timeout 5
   password @Cons-jeferson
   login
   exit
   enable secret @dmin-jeferson
   banner motd $	----------------------------------------------------------------
   | 															                                             |
   | Roteador Pato Branco 						                                           |
   | 															                                             |
   | ATENCAO Acesso Restrito a pessoas autorizadas! 				                     |
   | 															                                             |
   | Administrador: JEFERSON ROSA DE SOUZA (jefsou@alunos.utfpr.edu.br) 	       |
   | 															                                             |
   -----------------------------------------------------------------------------$
   ip domain name jeferson.souza.com.br
   crypto key generate rsa general-keys modulus 1024
   username jeferson secret ssh@Network1ng
   exit
   w
   ```

## Vitorino

1. Roteador

   ```bash
   enable
   conf t
   hostname r-vit-js
   ipv6 unicast-routing
   interface Se0/0/0
   description vit-fb
   clock rate 56000
   ip address 200.200.60.229 255.255.255.252
   ipv6 address 2001:DB8:ACAD:3CFF::1:1/112
   ipv6 enable
   no shutdown
   exit
   interface Se0/0/1
   description pb-vit
   ip address 200.200.60.226 255.255.255.252
   ipv6 address 2001:DB8:ACAD:3CFF::2/112
   ipv6 enable
   no shutdown
   exit
   ip route 200.200.60.0 255.255.255.192 200.200.60.230
   ip route 200.200.60.64 255.255.255.224 200.200.60.230
   ip route 200.200.60.96 255.255.255.224 200.200.60.230
   ip route 200.200.60.236 255.255.255.252 200.200.60.230
   ip route 200.200.60.232 255.255.255.252 200.200.60.230
   ip route 200.200.60.240 255.255.255.252 200.200.60.230
   ipv6 route 2001:DB8:ACAD:3C00::/64 2001:DB8:ACAD:3CFF::1:2
   ipv6 route 2001:DB8:ACAD:3C01::/64 2001:DB8:ACAD:3CFF::1:2
   ipv6 route 2001:DB8:ACAD:3C02::/64 2001:DB8:ACAD:3CFF::1:2
   ipv6 route 2001:DB8:ACAD:3CFF::3:0/112 2001:DB8:ACAD:3CFF::1:2
   ipv6 route 2001:DB8:ACAD:3CFF::2:0/112 2001:DB8:ACAD:3CFF::1:2
   ipv6 route 2001:DB8:ACAD:3CFF::4:0/112 2001:DB8:ACAD:3CFF::1:2

   security passwords min-length 10
   login block-for 120 attempts 3 within 60
   line vty 0 15
   exec-timeout 5
   login local
   transport input ssh
   exit
   service password-encryption
   line con 0
   exec-timeout 5
   password @Cons-jeferson
   login
   exit
   enable secret @dmin-jeferson
   banner motd $	----------------------------------------------------------------
   | 															                                             |
   | Roteador Vitorino 						                                             |
   | 															                                             |
   | ATENCAO Acesso Restrito a pessoas autorizadas! 				                     |
   | 															                                             |
   | Administrador: JEFERSON ROSA DE SOUZA (jefsou@alunos.utfpr.edu.br) 	       |
   | 															                                             |
   -----------------------------------------------------------------------------$
   ip domain name jeferson.souza.com.br
   crypto key generate rsa general-keys modulus 1024
   username jeferson secret ssh@Network1ng
   exit
   w
   ```

## Itapejara D`Oeste

1. Roteador

   ```bash
   enable
   conf t
   hostname r-ita-js
   ipv6 unicast-routing
   interface Se0/0/0
   description ita-pb
   clock rate 56000
   ip address 200.200.60.237 255.255.255.252
   ipv6 address 2001:DB8:ACAD:3CFF::3:1/112
   ipv6 enable
   no shutdown
   exit
   interface Se0/0/1
   description fb-ita
   ip address 200.200.60.234 255.255.255.252
   ipv6 address 2001:DB8:ACAD:3CFF::2:2/112
   ipv6 enable
   no shutdown
   exit
   interface fa0/1
   description cv-ita
   ip address 200.200.60.241 255.255.255.252
   ipv6 address 2001:DB8:ACAD:3CFF::4:1/112
   ipv6 enable
   no shutdown
   exit
   ip route 200.200.60.0 255.255.255.192 200.200.60.238
   ip route 200.200.60.64 255.255.255.224 200.200.60.238
   ip route 200.200.60.96 255.255.255.224 200.200.60.242
   ip route 200.200.60.224 255.255.255.252 200.200.60.238
   ip route 200.200.60.228 255.255.255.252 200.200.60.238
   ipv6 route 2001:DB8:ACAD:3C00::/64 2001:DB8:ACAD:3CFF::3:2
   ipv6 route 2001:DB8:ACAD:3C01::/64 2001:DB8:ACAD:3CFF::3:2
   ipv6 route 2001:DB8:ACAD:3C02::/64 2001:DB8:ACAD:3CFF::4:2
   ipv6 route 2001:DB8:ACAD:3CFF::/112 2001:DB8:ACAD:3CFF::3:2
   ipv6 route 2001:DB8:ACAD:3CFF::1:0/112 2001:DB8:ACAD:3CFF::3:2

   security passwords min-length 10
   login block-for 120 attempts 3 within 60
   line vty 0 15
   exec-timeout 5
   login local
   transport input ssh
   exit
   service password-encryption
   line con 0
   exec-timeout 5
   password @Cons-jeferson
   login
   exit
   enable secret @dmin-jeferson
   banner motd $	----------------------------------------------------------------
   | 															                                             |
   | Roteador Itapejara D`Oeste 						                                     |
   | 															                                             |
   | ATENCAO Acesso Restrito a pessoas autorizadas! 				                     |
   | 															                                             |
   | Administrador: JEFERSON ROSA DE SOUZA (jefsou@alunos.utfpr.edu.br) 	       |
   | 															                                             |
   -----------------------------------------------------------------------------$
   ip domain name jeferson.souza.com.br
   crypto key generate rsa general-keys modulus 1024
   username jeferson secret ssh@Network1ng
   exit
   w
   ```
