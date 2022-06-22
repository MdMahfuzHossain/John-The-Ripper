# 🔥John-The-Ripper

# ⤵️Welcome
    John the Ripper is one of the most well known, well-loved and versatile hash cracking tools out there. It combines a fast cracking speed, with     an extraordinary range of compatible hash types. 

# 🃏Setting up John the Ripper 
    sudo apt install john
    
# ⚔️Wordlists
    https://github.com/danielmiessler/SecLists
    sudo gzip -d /usr/share/wordlists/rockyou.txt.gz.

# 🦀Cracking Basic Hashes # John Basic Syntax
    john [options] [path to file]
    john - Invokes the John the Ripper program
    [path to file] - The file containing the hash you're trying to crack, if it's in the same directory you won't need to name a path, just the file.
    Note: Crack Hash store in john.pot file
    
# 🦀Automatic Cracking
    john --wordlist=[path to wordlist] [path to file]

    --wordlist= - Specifies using wordlist mode, reading from the file that you supply in the following path...

    [path to wordlist] - The path to the wordlist you're using, as described in the previous task.

    Example Usage:

    john --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt
    
# 🧨Format-Specific Cracking
    john --format=[format] --wordlist=[path to wordlist] [path to file]

    --format= - This is the flag to tell John that you're giving it a hash of a specific format, and to use the following format to crack it

    [format] - The format that the hash is in

    Example Usage:

    john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt
    
 # 🪟Cracking Windows Authentication Hashes
    This section is about cracking Windows hashes and NTHash / NTLM
    Example:
        john --format=nt --wordlist=rockyou.txt ntlm.txt
        
  # #️⃣Cracking Hashes from /etc/shadow
      Unshadowing:
          unshadow [path to passwd] [path to shadow]

          unshadow - Invokes the unshadow tool

          [path to passwd] - The file that contains the copy of the /etc/passwd file you've taken from the target machine

          [path to shadow] - The file that contains the copy of the /etc/shadow file you've taken from the target machine

          Example Usage:

          unshadow local_passwd local_shadow > unshadowed.txt
           
        Cracking:
           --format=sha512crypt

           john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt unshadowed.txt
           
# #️⃣Using Single Crack Mode
      john --single --format=[format] [path to file]

      --single - This flag lets john know you want to use the single hash cracking mode.

      Example Usage:

      john --single --format=raw-sha256 hashes.txt

      A Note on File Formats in Single Crack Mode:

      If you're cracking hashes in single crack mode, you need to change the file format that you're feeding john for it to understand what data         to create a wordlist from. You do this by prepending the hash with the username that the hash belongs to, so according to the above example-       we would change the file hashes.txt

      From:
  
        1efee03cdcb96d90ad48ccc7b8666033

      To

        mike:1efee03cdcb96d90ad48ccc7b8666033
        
# 🤐Cracking Password Protected Zip Files 
    Zip2John:
      zip2john [options] [zip file] > [output file]
    Example Usage:
      zip2john zipfile.zip > zip_hash.txt
      
    Cracking:
       john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt
      
# 🤐Cracking Password Protected RAR Archives
    Rar2John:
      rar2john [rar file] > [output file]
    Example Usage
      rar2john rarfile.rar > rar_hash.txt
      
    Cracking: 
      john --wordlist=/usr/share/wordlists/rockyou.txt rar_hash.txt

# 🔐Cracking SSH Keys with John 
    SSH2John:
      ssh2john [id_rsa private key file] > [output file]
    Example Usage
      ssh2john id_rsa > id_rsa_hash.txt
      
    Cracking:
      john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa_hash.txt

    
