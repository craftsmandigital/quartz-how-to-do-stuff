---
{"publish":true,"title":"Obsidian API, ingoing, outgoing","created":"2025-08-19","modified":"2025-08-19","tags":["#recipes"],"cssclasses":""}
---


## Connecting Obsidian REST API

This does it possible to connect to obsidian REST API using applications as N8N

<iframe width="560" height="315" src="https://www.youtube.com/embed/NyL0ovWYj7M?si=wHcqkpiUaBIEza47" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

### Here are some parameters to fill inn along with video

``` powershell
Bearer <<secret stuff>>

post-webhook:post-webhook-note-<<secret stuff>>

netsh interface portproxy add v4tov4 listenport=6888 listenaddress=0.0.0.0 connectport=6808 connectaddress=127.0.0.1

netsh advfirewall firewall add rule name="Obsidian HTTP Proxy" dir=in action=allow protocol=TCP localport=6888

ipconfig /all
	Ethernet adapter Ethernet:
		  IPv4 Address. . . . . . . . . . . : 192.168.1.131(Preferred)
		  
curl -H "Authorization: Bearer <<YOURAPI>>" http://192.168.1.131:6888

curl -H "Authorization: Bearer <<YOURAPI>>" https://obsidian.craftsmandigital.net
```

Her is my own [N8N test](https://n8n.craftsmandigital.net/workflow/YI2Nxvfpu1PZGnhI)


## Executing webhooks from obsidian

Description on how to use the [obsidian-post-webhook](https://github.com/Masterb1234/obsidian-post-webhook) plugin. The description is great but a little wage on authorization

- Configuring Auth on N8N
	- Create a **header auth** to use in the webhook node
	- Configure it as this
		- **Name**: "Authorization"
		- **Value**: "Bearer << your secret string >>"
		  example value: "Bearer sdfsfd88sgssses"
- Configuring auth in obsidian-post-webhook
	- In the webhook property **Custom heades** fill in this JSON:
	  `{"Authorization":"Bearer sdfsfd88sgssses"}`

Here is my own [N8N test with auth](https://n8n.craftsmandigital.net/workflow/QXUNLXtghh5vMZQO). Copied gmail workflow described from the [github repo](https://github.com/Masterb1234/obsidian-post-webhook?tab=readme-ov-file#email-integration) and added auth and emails in html format, not just plain text.