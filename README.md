# Installazione Arch

## Preparare la Macchina Virtuale con `virt-manager`

### File ISO da utilizzare

Arch Linux mensile, ad esempio:

`archlinux-2023.12.01-x86_64.iso`

### Caratteristiche della VM

> RAM 2048MB
> Core 2
> HD 20GM

**NB** Flaggare la configurazione dell'hardware prima di avviare l'installazione.

### Cartella condivisa

Nel componente _Memory_, flaggare _enable shared memory_.

Aggiungere hardware tipo _Filesystem_ e compilare come segue:

> Driver: `virtiofs`  
> Source path: `/home/max/shared`  
> Target path: `/shared`

Avviare l'installazione.

## Avvio installazione da ISO

```shell
# loadkeys it
# curl -LO https://raw.githubusercontent.com/max-matty/archinstaller/master/install_sys.sh
# sh install_sys.sh
```

## Primo avvio in caso di Macchina Virtuale

La scelta comporta il salvataggio della variabile `~/.screenlayout/var_inst` che viene verificata all'avvio della macchina per impostare, in ambiente 'X', la configurazione corretta dello schermo.

## Inizializzazione Neovim

Al primo avvio Neovim installa i plugins e Mason installa i server LSP.

Tramite `:Mason` rimane solamente da installare mamualmente:

- `markdownlint`
- `prettier`
- `shellcheck`

## Utilizzo di Spice Viewer

E' consigliabile fare partire la macchina dal visualizzatore _Spice_ per una migliore gestione del cambio di Workspace in `i3-wm` nella macchina _Host_.

E' già configurata in `i3-wm` (lato _Host_) la combinazione tasti `$mod+Control+[0-9]` per avviare 10 VM.

Per collegare la singola VM è sufficiente impostare da `virt-manager` la porta _Spice_ all'interno del componente _Display Spice_, esempio: 5900 per la combinazione `$mod+Control+0` fino a 5009 per la combinazione `$mod+Control+9`.

## Utilizzo di ssh

Per fare partire la macchina in background digitare:

`$ virsh -c qemu:///system start <VM-name>`

Successivamente possiamo fare l'accesso da terminale:

`$ ssh max@<ip-guest>`

Per trovare l'indirizzo IP sulla rete digitare:

`$ arp -n`

Sono stati configurati sulla macchina _Host_ gli _alias_ per fare partire le 10 macchine virtuali e per stopparle come segue: `startVM-00` e `stopVM-00`.

### Files Multimediali

Quando ci colleghiamo tramite `ssh` è impostata di default la possibilità di eseguire applicazioni grafiche utilizzando il Server X della macchina _Host_.

## Github

Al primo utilizzo ci verrà chiesto di inserire nome ed indirizzo email.
