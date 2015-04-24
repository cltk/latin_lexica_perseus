The file latin\_english\_lexicon\_old.xml comes from Perseus, where is was called 1999.04.0059.xml ([http://sourceforge.net/projects/perseus-hopper/](source here)) and licensed under the [Mozilla Public License 1.1 (MPL 1.1)](http://www.mozilla.org/MPL/1.1/).

## Parsing

To parse with Python, the following works:

```
from lxml import etree
from io import StringIO
import os

old_path = os.path.expanduser('~/cltk_data/latin/lexicon/latin_lexica_perseus/latin_english_lexicon_old.xml')
with open(old_path) as f:
    old_xml = f.read()
tree = etree.parse(StringIO(old_xml))

entries = tree.xpath('/TEI.2/text/body/div0/entryFree')

print(len(entries))  # 51594

for x in entries:
    print(x.get('key'))
    input()
```
