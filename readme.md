# Setup
    podman volume create --driver local -o o=bind -o type=none -o device="$(readlink -f .)/" zmk-config
    podman volume create --driver local -o o=bind -o type=none -o device="$(readlink -f ../zmk-modules)/" zmk-modules  


# Buildcommands
    cd /workspaces/zmk/app

## settings_reset
    west build -p -d build/settings_reset_nn -b nice_nano_v2 -- -DSHIELD=settings_reset
    west build -p -d build/settings_reset_xiao -b seeeduino_xiao_ble -- -DSHIELD=settings_reset

## Arkenswoop
    west build -p -d build/arkenswoop_dongle -b seeeduino_xiao_ble -- -DSHIELD="arkenswoop_dongle dongle_screen" -DZMK_CONFIG="/workspaces/zmk-config/config" -DZMK_EXTRA_MODULES="/workspaces/zmk-modules/zmk-auto-layer;/workspaces/zmk-modules/zmk-dongle-screen;/workspaces/zmk-modules/zmk-helpers;/workspaces/zmk-modules/zmk-keyboard-arkenswoop;/workspaces/zmk-modules/zmk-tri-state"
    for half in left right; do west build -p -d build/arkenswoop_${half} -b nice_nano_v2 -- -DSHIELD="arkenswoop_${half}" -DZMK_CONFIG="/workspaces/zmk-config/config" -DZMK_EXTRA_MODULES="/workspaces/zmk-modules/zmk-auto-layer;/workspaces/zmk-modules/zmk-dongle-screen;/workspaces/zmk-modules/zmk-helpers;/workspaces/zmk-modules/zmk-keyboard-arkenswoop;/workspaces/zmk-modules/zmk-tri-state"; done

## Kyria rev3
    for half in left right; do west build -p -d build/kyria_rev3_${half} -b nice_nano_v2 -- -DSHIELD="kyria_rev3_${half}" -DZMK_CONFIG="/workspaces/zmk-config/config" -DZMK_EXTRA_MODULES="/workspaces/zmk-modules/zmk-auto-layer;/workspaces/zmk-modules/zmk-helpers;/workspaces/zmk-modules/zmk-tri-state"; done
