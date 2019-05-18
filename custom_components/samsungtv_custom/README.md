# Samsung TV - custom integration

This integration allows you to connect your Samsung Smart TV (UE55MU6102K) to Home Assistant. It operates using WSS protocol only.

If you use this integration, make sure you perform required changes:

 - `manifest.json`: install [samsung-tv-api](https://github.com/marysieek/samsung-tv-api),
 - `configuration.yml`: add required entry and update token.

### Installation

1. Copy this folder to `<config_dir>/custom_components/samsungtv_custom/`.

2. Add the following entry in your `configuration.yaml`:

```yaml
media_player:
  - platform: samsungtv_custom
    host: HOST_HERE
    name: NAME_HERE
    port: PORT_HERE
    password: TOKEN_HERE
```

3. Update your config file with your token.

### Finding your token

1. Create sample file:

```bash
touch example.py
```

2. Add following code inside your example.py file:

```python
from samsungtv import SamsungTV

tv = SamsungTV('192.168.X.X')
tv.menu()
```

3. Execute your script - make sure your TV is ON:

```bash
python3 example.py
```

4. A dialog box will come up prompting you to accept the connection.

5. Your token will be printed out - add it as password to `configuration.yaml` file.
