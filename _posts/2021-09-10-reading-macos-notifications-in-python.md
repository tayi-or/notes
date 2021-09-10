Python code snippet for reading notifications in Python3. Works on Big Sur.
```py
# Read macOS Notifications
# Author: Taylor Robinson
# pip3 install bpylist

import sqlite3
import os
from bpylist import bplist

userDir = os.popen("getconf DARWIN_USER_DIR").read().strip()
file = userDir + "com.apple.notificationcenter/db2/db"
print("Opening",file)

db = sqlite3.connect(f'file:{file}?mode=ro', uri=True)

notifs = [{
    "rec_id": row[0],
    "app_id": row[1],
    "uuid": row[2],
    "data": bplist.parse(row[3]),
    "request_date": row[4],
    "request_last_date": row[5],
    "delivered_date": row[6],
    "presented": row[7],
    "style": row[8],
    "snooze_fire_date": row[9],
} for row in db.execute("SELECT * FROM record").fetchall()]

print(notifs[0]["data"]);

for notif in notifs:
    data = notif["data"]
    app = data["app"] if "app" in data else "Unknown App"
    title =  data["req"]["titl"] if "titl" in data["req"] else "" 
    body = data["req"]["body"] if "body" in data["req"] else ""
    print(f"{app}: {title}")
    print("\t" + body.replace("\n",""))
    if 'scat' in data['req'] and 'acts' in data["req"]["scat"]:
        for act in data["req"]["scat"]["acts"]:
            print("\t [", act, "]")
    print("")

# Example notification object
{
    'styl': 2,
    'intl': True,
    'app': '_SYSTEM_CENTER_:com.apple.DiskArbitration.DiskArbitrationAgent',
    'uuid': '(binary string)',
    'resp': {
        'act': 0,
        'for': True
    },
    'srce': '(binary string)',
    'req': {
        'atta': [{
            'pur': 1,
            'fam': 0,
            'uti': 'public.image',
            'nsst': 1,
            'pat': '/System/Library/CoreServices/CoreTypes.bundle/Contents/Resources/FinderIcon.icns'
        }],
        'body': 'Eject “Install macOS Mojave” before disconnecting or turning it off.',
        'nsdict': {
            'nsper': False
        },
        'ddac': False,
        'scat': {
            'id': 'LEGACY',
            'opt': 132,
            'un_ha': False
        },
        'titl': 'Disk Not Ejected Properly'
    },
    'date': 631718723.800089,
    'orig': 4
} 

{
    'styl': 1,
    'intl': True,
    'app': 'com.apple.Music',
    'uuid': 'binary string',
    'resp': {
        'act': 0,
        'for': True
    },
    'srce': 'binary string',
    'req': {
        'atta': [{
            'data': '(png)',
            'fam': 0,
            'uti': 'public.image',
            'pur': 0
        }],
        'usda': '(bplist)',
        'ddac': False,
        'scat': {
            'id': 'LEGACY',
            'opt': 148,
            'acts': [{
                'id': 'ACTION',
                'ti': 'Skip'
            }]
        },
        'titl': 'Where I Belong',
        'subt': 'Protostar & Emma McGann — Monstercat Instinct Vol. 5'
    },
    'date': 652922977.088903,
    'orig': 4
}
```
