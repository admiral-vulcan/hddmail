# hddmail
Checks HDDs and sends info mails

## SMART status evaluation

`hddexec` now queries `smartctl` in JSON mode and stores a structured summary in
`/bin/hddmailFiles/hddsummary.txt` and `/bin/hddmailFiles/hddstatus.txt`. The
summary lists healthy indicators such as overall SMART health, power-on hours
and temperature for every configured drive. The status file only contains
entries for pre-fail conditions like failed attributes, non-zero ATA/NVMe error
counters or smartctl errors.

Example status excerpt:

```
Status of /dev/sda:
  - SMART overall-health check reports FAILURE
  - Reallocated_Sector_Ct: raw value 4

Status of /dev/nvme0n1:
  - NVMe critical warning flags set: 1
  - NVMe media errors: 8
```

The generated HTML report highlights affected drives in red and healthy drives
in green. The email subject automatically reports how many disks triggered a
warning so harmless counters (for example constant CRC values) no longer appear
as failures.

To inspect the plain-text report locally after running `hddexec`, open
`/bin/hddmailFiles/hddmail.txt`. The HTML version (used for emails) is stored in
`/bin/hddmailFiles/hddmailsend.txt` and contains the same data in table form.
