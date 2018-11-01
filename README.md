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
  validates_presence_of :name, :login, :message => 'required'
  validates_presence_of :password, :password_confirmation, :message => 'required', :if => :new_record?
  validates_format_of :email, :message => 'invalid e-mail address', :allow_nil => true, :with => /^$|^([^@\s]+)@((?:[-a-z0-9]+\.)+[a-z]{2,})/i
  validates_length_of :name, :maximum => 100, :allow_nil => true, :message => '%d-character limit'
  validates_length_of :login, :within => 3..40, :allow_nil => true, :too_long => '%d-character limit', :too_short => '%d-character minimum'
  validates_length_of :password, :within => 5..40, :allow_nil => true, :too_long => '%d-character limit', :too_short => '%d-character minimum', :if => :validate_length_ofpassword?
  validates_length_of :email, :maximum => 255, :allow_nil => true, :message => '%d-character limit'
  validates_numericality_of :id, :only_integer => true, :allow_nil => true, :message => 'must be a number'
end

# custom_tags_extension.rb
class CustomTagsExtension < Radiant::Extension
  version "1.0"
  description "Describe your extension here"
  url "http://yourwebsite.com/custom_tags"
  def activate
    # admin.tabs.add "Custom Tags", "/admin/custom_tags", :after => "Layouts", :visibility => [:all]
  end
  def dectivate
    # admin.tabs.remove "Custom Tags"
  end
end

require File.dirname(__FILE__) + '/../spec_helper'
describe 'CustomTags' do
  dataset :pages
  describe '<r:box>' do
    it 'should render the correct HTML' do
      tag = '<r:box icon="happyface" title="Test Title"></r:box>'
      expected = %{<div class="box">}
  <h2>
    <img src="/images/icons/happyface.png" />
    Test Title
  </h2>
  <div class="content">
  <div class="content">
    Content
  </div>
</div>}
      pages(:home).should render(tag).as(expected)
    end
  end
end

module CustomTags
  include Radiant::Taggable
  desc "Creates an HTML box with a title, icon and body content"
  tag "box" do |tag|
    ""
  end
end

Page.send :include, CustomTags

de activate
  admin.tags.add "Custom Tags", "/admin/custom_tags"
end

admin.tabs["Snippets"].visibility = [:developer, :admin]


```

```
```

```
```


