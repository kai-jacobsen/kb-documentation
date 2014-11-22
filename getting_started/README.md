# Getting Started

###Important note / Expectation

Again, if you missed the introduction: If you don't do code, stop right now.  
Start in a local sandbox or dev environment to get an idea of the basic concepts.

We're not talking about details during the quick start, just some copy & paste snippets to get you going.

###Requirements

* Wordpress 3.9+ (4.0 recommended)
* PHP 5.4+

###Example theme

You can find a very basic example theme with plugin integration, based on Twentyfourteen, here:

https://github.com/kai-jacobsen/kbfourteen.git

###Installation

You will need composer.

I. Download a copy of the repository or clone it to your local WordPress plugin directory  
```
cd /path/to/wp-content/plugins    
git clone https://github.com/kai-jacobsen/kontentblocks.git kontentblocks  
cd kontentblocks && composer install```

If you manage your composer dependencies in a project/full-stack vendor directory (using custom composer installers) you simply can add the following to your composer.json

```
"repositories": [
        {
            "type": "composer",
            "url": "http://composer.kontentblocks.de"
        }
    ]
```

require package:

```
"jcbsn/kontentblocks" : "dev-master"```


