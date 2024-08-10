# Arcade Hero: Enter the Cloud Function Ruby || [ARC234](https://www.cloudskillsboost.google/focuses/98836?catalog_rank=%7B%22rank%22%3A1%2C%22num_filters%22%3A0%2C%22has_search%22%3Atrue%7D&parent=catalog&search_id=34942183) ||

# # Like, comment, share & Don't forget to subscribe [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN) 👍😄🤝

### Run the following Commands in CloudShell

```
export REGION=
```
```

gcloud config set compute/region $REGION
export PROJECT_ID=$(gcloud config get-value project)

mkdir quicklab && cd quicklab

cat > Gemfile <<'EOF_END'
source "https://rubygems.org"
gem "functions_framework", "~> 0.7"
EOF_END


cat > Gemfile.lock <<'EOF_END'
GEM
  remote: https://rubygems.org/
  specs:
    cloud_events (0.7.0)
    functions_framework (1.2.0)
      cloud_events (>= 0.7.0, < 2.a)
      puma (>= 4.3.0, < 6.a)
      rack (~> 2.1)
    nio4r (2.5.8)
    puma (5.6.5)
      nio4r (~> 2.0)
    rack (2.2.6.4)

PLATFORMS
  ruby
  x86_64-linux

DEPENDENCIES
  functions_framework (~> 1.2)

BUNDLED WITH
   2.4.6

EOF_END

cat > app.rb <<'EOF_END'
require "functions_framework"
require "cgi"
require "json"

FunctionsFramework.http "hello_http" do |request|
  # The request parameter is a Rack::Request object.
  # See https://www.rubydoc.info/gems/rack/Rack/Request
  name = request.params["name"] ||
         (request.body.rewind && JSON.parse(request.body.read)["name"] rescue nil) ||
         "World"
  # Return the response body as a string.
  # You can also return a Rack::Response object, a Rack response array, or
  # a hash which will be JSON-encoded into a response.
  "Hello #{CGI.escape_html name}!"
end
EOF_END

bundle install

gcloud functions deploy cf-demo \
  --gen2 \
  --runtime ruby33 \
  --entry-point hello_http \
  --source . \
  --region $REGION \
  --trigger-http \
  --allow-unauthenticated \
  --quiet

```

# Congratulations ..!!🎉  You completed the lab shortly..😃💯

# *Well done..!* 👏

# Thank you for visiting.... :) 🗯️

# [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN)
