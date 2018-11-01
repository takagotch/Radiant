### radiant
---
http://radiantcms.org/

```ruby
class User < ActiveRecord::Base
  order_by 'name'
  
  belongs_to :created_by, :class_name => 'User'
  belongs_to :updated_by, :class_name => 'User'
  
  validates_uniqueness_of :login, :message => 'login already in use'
  validates_configumation_of :password, :message => 'must match confirmation', :if => :confirm_password?
  
end

```

```
```

```
```


