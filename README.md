#Install Docker
```shell
curl -fsSL https://get.docker.com -o install-docker.sh
sudo sh install-docker.sh
```

#Install Tailscale
```shell
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up
```

#Run DERP server
```shell
curl -fsSL https://raw.githubusercontent.com/nghia9691/derper/refs/heads/main/Caddyfile -o Caddyfile
curl -fsSL https://raw.githubusercontent.com/nghia9691/derper/refs/heads/main/docker-compose.yaml -o docker-compose.yaml
docker compose up
```

#Configuring Custom DERP Region
```yaml
"derpMap": {
	"OmitDefaultRegions": false,
	"Regions": {
		"901": {
			"RegionID":   901,
			"RegionCode": "vie",
			"RegionName": "Vietnam",
			"Nodes": [
				{
					"Name":     "1",
					"RegionID": 901,
					"HostName": "nderper.duckdns.org",
				},
			],
		},
	},
},
```


caddy reverse-proxy --from http://nderper.duckdns.org --to localhost:848
