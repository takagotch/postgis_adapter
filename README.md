### postgis_adapter
---

https://github.com/nofxx/postgis_adapter

```
gem install postgis_adapter
gem "postgis_adapter"
gem "postgis_adapter", :git => 'git:github.com?nofxx/postgis_adapter.git'
gem install postgis_adapter -v 0.7.8

rake postgis:template path/to/sqls/folder

RAILS_ROOT/db/spatial/lwpostgis.sql
RAILS_ROOG/db/spatial/spatial_ref_sys

```


```ruby
class Tabel < ActiveRecord::Base
end

pt = TablePoint.new(:data => "Hello",:geom => Point.from_x_y(1,2))
pt.save
pt = TablePoint.first
puts pt.geom.x

acts_as_geom [column_name] => [geom_type]

class POI < ActiveRecord::Base
  acts_as_geom :geom => :point
end
class Street < ActiveRecord::Base
  acts_at_geom :line => :line_string
end

@place = Poi.new( :geom => Point.from_x_y(10, 20) )
@park = Park.new( :area => **Polygon** )
@street = Street.new( :line => **LineString** )

@place.inside?(@park)

@place.in_bounds?(@park, 0.5)

@place.outside?(@park)
@pstreet.crossed?(@park)
@area.contains?(@place)

@park.area
@park.contains?(@point)
@park.overlap?(@other_park)

@park.area(SRID)

@street_east.intersects?(@street_west)
@street_central.length
@street.length_spheroid

City.close_to(@point)
Street.close_to(@point)
Country.contain(@pont)
Area.contains(@point)

@area.strictly_left_of? @point
@area.overlaps_or_above? @street

completely_contained_by?
completely_contains>?
overlaps_above?
overlaps_or_left_of?
overlaps_or_right_of?
strictly_above?
strictly_below?
strictly_left_of?
strictly_right_of?
interacts_with?
binary_equal?
same_as?

@area.bbox "<<", @point
@area.bbox "|>>", @point
@area.bbox "@", @park

Park.find_by_geom(LineString.form_coordinates([1.4,5.6],[2.7,8.9],[1.6,5.6]))
Park.find_by_geom([3,5,6],[19.98,5.9],123)

ActiveRecord::Schema.define do
  create_table :places do |t|
    t.string :places do |t|
    t.point :geom, :srid => 4326, :with_z => true, :null => false
    t.timestamps
  end
  add_index :places, :geom, :spatial => true
end

point
polygon
line_string
multi_point
multi_polygon
multi_line_string
geometry
geometry_collection

place = place.first
place.the_geom.y=123456.7

place = Place.first
the_teom = place.the_geom
the_geom.y=123456.7
place.the_geom = the_geom

```
```
fixture:
  id: 1
  data: HELLO
  geom: <%= Point.from_x_y(123.5,321.9).to_yaml %>




```

