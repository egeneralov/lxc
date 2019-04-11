# egeneralov.lxc

Provision LXC installation.

## Requirements

Debian 8/9.

## Role Variables

Just (re)place config. 

- **lxc**:
  - **net**:
    - `{l: '', r: '^'}`
  - **conf**:
    - `{l: '', r: '^'}`

### installation with NAT networking

Just use default values.

    - hosts: servers
      roles:
         - egeneralov.lxc

### installation with existing bridge

Replace `br0` with your own value.

    - hosts: servers
      vars:
        lxc:
          net:
            - {l: 'USE_LXC_BRIDGE="false"', r: '^USE_LXC_BRIDGE.*'}
          conf:
            - {l: 'lxc.network.type = veth', r: '^lxc.network.type.*'}
            - {l: 'lxc.network.flags = up', r: '^lxc.network.flags.*'}
            - {l: 'lxc.network.link = br0', r: '^lxc.network.link.*'}
            - {l: 'lxc.network.hwaddr = 00:FF:AA:00:xx:xx', r: '^lxc.network.hwaddr.*'}
      roles:
         - egeneralov.lxc

## License

MIT

## Author Information

Eduard Generalov <eduard@generalov.net>
