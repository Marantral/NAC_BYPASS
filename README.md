# NAC_BYPASS
Network Access Control bypass.  HowTo and discussions

## Network Access Control (NAC) Bypass

NAC leverages IEEE 802.1X with different extensible authentication protocols (EAP) Protected EAP (PEAP) being the one I have seen the most.  NAC is designed to only allow approved devices onto your network. If you have sat through any marketing presentations of NAC from Cisco or Aruba you would assume that this is a well oiled machine that is a silver bullet for all unauthorized devices on your network. However, this amounts to just a fairy tale and just like the tooth fairy its not real. It does make it harder to get onto a network, but is not a silver bullet and will not stop a motivated attacker. 

## How does it work?
There are three parts of NAC 1. Supplicant (END POINT) 2. Authenticator (Switch or Access point) 3. Authentication server (RADIUS). In simple terms the port of the authenticator only allows EAPOL traffic (Just means EAP over LAN (I know that is silly)) over the port. This traffic is forwarded to whatever authentication server the authenticator is configured for. Once the authentication server makes a decision on authentication and authorization it sends commands to the authentcator to allow or deny the connection and to place any additional configuration on the port. If the endpoint does not support supplicant software the authenticator will use MAC Authentication Bypass (MAB) if it is configured to do so. This is almost like classic mac based port security, but the mac is approved or denied by the authentication server. 

### Weak points:
#### Admin Configurations
a. Admins tend to only configure user ports for NAC and do not think about unused ports or port in “Secured” areas. </br>
b. Overly permissive access control lists. 

#### MAB:
Mac addresses are easily spoofed, you can also spoof other common system checks (Host information). 

#### Authenticator:
Switches can be tricked and give you the ability to ride an authorized user’s authentication (ISE skating).
