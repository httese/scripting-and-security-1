# Comprobar si un puerto TCP está abierto
## Java, Network 
### URL: https://www.jesusninoc.com/2012/10/10/comprobar-si-un-puerto-tcp-esta-abierto/
```Java
import java.io.*; 
import java.net.*;

public class PuertoAbierto
{
	public static void main(String[] args)
	{
		int puerto=2050;
		try
		{
			Socket clientSocket = new Socket("192.168.1.37",puerto);
			PrintWriter out = new PrintWriter(clientSocket.getOutputStream(),true);
			System.out.println("Puerto " + puerto + " abierto");
			out.close();
			clientSocket.close();
			}
		catch (UnknownHostException e){
			System.out.println(e);
		}
		catch (IOException e) {
			System.out.println("Puerto " + puerto + " cerrado");
		}
		}
	}

```
# Comprobar si un puerto TCP está abierto
## Network, PowerShell, Security 
### URL: https://www.jesusninoc.com/2015/01/14/comprobar-si-un-puerto-esta-abierto/
```PowerShell
1..1024 | % {Write-Host ((new-object Net.Sockets.TcpClient).Connect('10.0.0.3',$_)) '$_ abierto'}

```
