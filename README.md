osmosis with mapsforge support.

* This image is based on Ubuntu 16.04.
* Default working folder /data

# Usage
    # Bash access
    docker run -t -i --rm -v `pwd`:/data osmtw/osmosis
    # run a command.
    docker run -t -i --rm -v `pwd`:/data osmtw/osmosis osmosis --read-pbf yms.osm.pbf --read-pbf yms_contour_lon121.50_121.60lat25.10_25.20_local-source.osm.pbf --merge --write-pbf yms.pbf
    
# Source

* Osmosis - OpenStreetMap Wiki - http://wiki.openstreetmap.org/wiki/Osmosis
* openstreetmap/osmosis https://github.com/openstreetmap/osmosis

* mapsforge - OpenStreetMap Wiki - https://wiki.openstreetmap.org/wiki/Mapsforge
* mapsforge/mapsforge: Vector map library written in Java - running on Android and Desktop. - https://github.com/mapsforge/mapsforge
