

## Scaffold

* `rails generate scaffold ticket name:string address:text paid:decimal  `
* `rails g …`
* `rails destory(d) …`
* `rake db:migrate`
* `rails g migration AddPhoneToTickets phone:string` (Then Change the Views)

## No Scaffold

### Model
* `rails g model ad name:string description:text price:decimal seller_id:integer` (Then migrate)
### Controller
* `rails g controller ads` (The model is ad and the controller is ads)
### Routes
		match '/ads/' => 'ads#index' 
		match '/ads/:id' => 'ads#show'
		match '/ads/:id/new' => 'ads#new'
		match '/ads/:id/create' => 'ads#create' 
		match '/ads/:id/delete' => 'ads#destory'
		match '/ads/:id/edit' => 'ads#edit'
		match 'ads/:id/update' => 'ads#update'
  		
### Controller:
	class AdsController < ApplicationController

	before_filter :check_logged_in, :only => [:edit, :update, :destory]
	
	def new
		@ad = Ad.new
	end
	
	def create
		@ad = Ad.new(params[:id])
		@ad.save
		redirect_to "/ads/#{@ad.id}"
	end

	def edit
		@ad = Ad.find(params[:id])
	end
	
	def update
		@ad = Ad.find(params[:id])
		@ad.update_attributes(params[:ad])
		redirect_to '/ads/#{@ad.id}'
	end
	
	
	def show
		@ad = Ad.find(params[:id])	
	end
	
	def index
		@ads = Ad.find(:all)
	end

	def destory
		@ad = Ad.find(params[:id])
		@ad.destory
		redirect_to '/ads/'
	end
	
	private
	def check_logged_in
		authenticate_or_request_with_http_basic("Ads") do |username, password|
			username ="oa414"
			password = "888888"
		end
	end
	
	
end

### View

	= form_for(@ad, :url => (:action=> create[update])) do |f|
	XXXXXX f.text_field :name
	XXXXXX f.text_area :description
	f.submit  "Create"
	
### Search

	= form_tag "/client_workouts/find" do # form_tag is the form that doesn't have model relation
		text_fielad_tag :search_string
		submit_tag "Search"
		
	
The controller


	@client_workouts =ClientWorkouts.find_all_by_client_name(param[:search_string)
	
	@client_workouts = Client_workouts.find(:all, :conditions => ["client_name = ? OR trainer =?", params[:search_string], param[:search_string]])
	
The View
	
	list a form


### Validates


## View

* render :partial->"new_seat"	# render _new_seat