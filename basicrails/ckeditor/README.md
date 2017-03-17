ADDING RAILS_ADMIN GEM TO YOUR GEMFILE
On your gemfile: gem 'rails_admin', '~> 1.1.1'
Run bundle install
Run rails g rails_admin:install
Provide a namespace for the routes when asked
Start a server rails s and administer your data at /admin. (if you chose default namespace: /admin)
ADDING CK EDITOR TO YOUR GEM FILE 
gem 'ckeditor', github: 'galetahub/ckeditor'
TO GENERATE MODELS TO STORE UPLOADED FILES

ActiveRecord + paperclip

To use the active_record orm with paperclip (i.e. the default settings):

ADD gem 'paperclip'

rails generate ckeditor:install --orm=active_record --backend=paperclip
LOAD EDITOR FROM GEM VENDOR
Include ckeditor javascripts in your app/assets/javascripts/application.js:

//= require ckeditor/init
IN THE FILE VIEWS/_FORM.HTML.ERB
REPLACE FORM.TEXT_AREA INTO  form.cktext_area

ADDING CKTEXTEDITOR TO RAILS_ADMIN
IN CONFIG/INITIALIZERS/RAILS_ADMIN.RB
ADD
RailsAdmin.config do |config|
  config.model your model name do
    edit do
      # For RailsAdmin >= 0.5.0
      field :your column name, :ck_editor
      # For RailsAdmin < 0.5.0
      # field :description do
      #   ckeditor true
      # end
    end
  end
end
