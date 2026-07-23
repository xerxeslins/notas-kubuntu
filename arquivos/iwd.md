## NetworkManager: Substituir wpa_supplicant por iwd (Kubuntu)

Vantagens técnicas do `iwd`:
* Foco exclusivo no kernel Linux.
* Operações assíncronas (scan e handshake mais rápidos).
* Roaming otimizado (802.11r) para transição fluida entre pontos de acesso.
* Menor consumo de recursos e integração nativa com API de criptografia do kernel.

```bash
sudo apt install iwd -y
sudo systemctl enable --now iwd

cat << 'EOF' | sudo tee /etc/NetworkManager/conf.d/iwd.conf
[device]
wifi.backend=iwd
EOF

sudo systemctl restart NetworkManager

```
