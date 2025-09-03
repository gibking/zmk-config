# Buildcommands

## settings_reset
    west build -d /workspaces/zmk/app/build/settings_reset -b nice_nano_v2 -- -DSHIELD=settings_reset

## Arkenswoop
    for half in left right; do west build -d /workspaces/zmk/app/build/arkenswoop_${half} -b nice_nano_v2 -- -DSHIELD="arkenswoop_${half} nice_view_adapter nice_view" -DZMK_CONFIG="/workspaces/zmk-config/" -DZMK_EXTRA_MODULES="/workspaces/zmk-modules/zmk-keyboard-arkenswoop/;/workspaces/zmk-modules/zmk-auto-layer/;/workspaces/zmk-modules/zmk-helpers/;/workspaces/zmk-modules/zmk-tri-state/"; done

## Kyria rev3
    for half in left right; do west build -d /workspaces/zmk/app/build/kyria_rev3_${half} -b nice_nano_v2 -- -DSHIELD="kyria_rev3_${half}" -DZMK_CONFIG="/workspaces/zmk-config/" -DZMK_EXTRA_MODULES="/workspaces/zmk-modules/zmk-keyboard-arkenswoop/;/workspaces/zmk-modules/zmk-auto-layer/;/workspaces/zmk-modules/zmk-helpers/;/workspaces/zmk-modules/zmk-tri-state/"; done
