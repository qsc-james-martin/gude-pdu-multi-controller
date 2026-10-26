# Gude PDU Multi Controller

## One panel for every Gude PDU in the design.

Power cycling a rack, or a whole building, should not mean opening a Gude plugin per PDU and pressing buttons in each one.

Each Gude Expert Power Control plugin controls a single PDU. With a dozen of them in a design, switching a group on or off, leaving one critical outlet alone, or checking whether everything is healthy turns into a lot of clicking and a lot of wiring.

**The Gude PDU Multi Controller is a Q-SYS plugin that sits on top of your existing Gude PDU plugins.** Pick which PDUs it controls, then switch them one by one, in groups, or all at once from a single panel, with combined status and usage in one place.

### What you get
- **Select and switch.** Select any PDUs and press On or Off. Every row also has its own On, Off and power toggle.
- **Press and hold for All On / All Off.** A deliberate hold, so nobody powers down the building by accident. A text box decides which PDUs are included, such as `1-9` or `1-4, 6-9`.
- **Outlet exceptions.** Choose which outlets get switched, globally or per PDU, such as `all except 1`. Leave the trainer's first outlet alone, for example.
- **Combined status.** One status for every PDU, with the problem PDUs listed.
- **Optional metering.** Total power, current, energy and average voltage across all PDUs.

# In detail

## Setup

Set **PDU Count** (default 4) in the plugin properties. On the Setup page, pick a Gude plugin for each row from the dropdown. Only Gude PDU plugins are listed. Give each row a display name if you like.

Each Gude plugin needs **Script Access** set to Script or All, otherwise this plugin cannot see its controls.

## Choosing outlets

Outlet lists accept plain text:

- `all` or `none`
- `1-6` or `1-4, 6-9`
- `all except 1` or `!1, !8`

Set a default for On and a default for Off, then override either per PDU. Leave a per-PDU box blank to use the default. The Setup page shows the resolved list for each PDU so you can check it before using it.

Because On and Off lists are separate, a PDU can be switched "off" while one outlet stays powered. The PDU's LED and state read Off once everything in its Off list is off.

## All On / All Off

Press and hold either button for the hold time (default 2 seconds). A progress bar fills while you hold, and letting go early cancels. PDUs are switched in turn with a short stagger (default 0.1 seconds) so a whole rack doesn't power up in the same instant.

## Status

Each row mirrors the status of its Gude plugin. The combined status is OK when all are OK, Compromised when some are not, and Fault when none are. In emulation it reports OK so designs can be tested without hardware.

## Metering

Metering is off by default. Turn it on in the plugin properties to add power, current, energy and voltage per PDU and in total. Choose whether readings come from the PDU inlets or from the sum of its outlets on the Setup page.

## Other settings

- **Deselect After On/Off.** Off by default, so your selection stays put after switching.
- **Hold Time, Stagger and Poll Interval.** Adjustable on the Setup page.
- **Debug Print.** A property that writes what the plugin is doing to the Q-SYS log.

The plugin only controls Gude plugins already in the design. It does not talk to the PDUs directly.
