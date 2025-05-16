##### - **Email notification via email gmail with nullmailer**
![[Pasted image 20250504163352.png]]
- install nullmailer on host install checkmk
	- file remotes 
	  ```bash
	  smtp.gmail.com smtp port=465 ssl auth-login user="phongict46@gmail.com" pass="tyqt rgjv xvrf bwhc"
		```
	- file default domain 
	  ```bash
	  gmail.com
		```
	- file mailname
	  ```bash
	  smtp.gmail.com
		``` 
	- file pausetime
	  ```bash
	  180
		```
	- file sendtimeout
	  ```bash
	  3600
		```


![[Pasted image 20250504164521.png]]



WARNING: Could not find logstash.yml which is typically located in $LS_HOME/config or /etc/logstash. You can specify the path using --path.settings. Continuing using the defaults

Could not find log4j2 configuration at path /usr/share/logstash/config/log4j2.properties. Using default config which logs errors to the console

[FATAL] 2025-05-13 16:01:01.275 [main] runner - An unexpected error occurred! {:error=>#<RuntimeError: Logstash cannot be run as superuser.>, :backtrace=>["/usr/share/logstash/logstash-core/lib/logstash/runner.rb:430:in `running_as_superuser'", "/usr/share/logstash/logstash-core/lib/logstash/runner.rb:259:in `execute'", "/usr/share/logstash/vendor/bundle/jruby/3.1.0/gems/clamp-1.3.2/lib/clamp/command.rb:66:in `run'", "/usr/share/logstash/logstash-core/lib/logstash/runner.rb:249:in `run'", "/usr/share/logstash/vendor/bundle/jruby/3.1.0/gems/clamp-1.3.2/lib/clamp/command.rb:140:in `run'", "/usr/share/logstash/lib/bootstrap/environment.rb:89:in `<main>'"]}

[FATAL] 2025-05-13 16:01:01.282 [main] Logstash - Logstash stopped processing because of an error: (SystemExit) exit

org.jruby.exceptions.SystemExit: (SystemExit) exit

        at org.jruby.RubyKernel.exit(org/jruby/RubyKernel.java:924) ~[jruby.jar:?]

        at org.jruby.RubyKernel.exit(org/jruby/RubyKernel.java:883) ~[jruby.jar:?]

        at usr.share.logstash.lib.bootstrap.environment.<main>(/usr/share/logstash/lib/bootstrap/environment.rb:90) ~[?:?]