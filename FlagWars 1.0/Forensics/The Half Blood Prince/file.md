Challenge name: Half Blood Prince

Challenge type: CRYPTOGRAPHY

Description:
A leak from the Order Archives claims that the identity of the Half-Blood Prince is hidden in an old potion lab book image. Another post hints at a secret chamber beneath a historic site where muggle victims were trapped — the “Chamber” was referenced in an encrypted diary entry. Harry Potter wants investigators to find both the Prince’s name and the Chamber’s location and recover the two flags before the leak spreads. Help Harry to find the answer before he goes to the next target.

Solution :
Step 1: In the TOM RIDDLE'S DIARY.txt you might find the cipher text "frirehf_fancr_".

Step 2: Using the online decoder {https://gchq.github.io/CyberChef/} decode the given cipher text which has been encoded in ROT 13. Then you get "severus_snape_" the name of the half blood prince.

Step 3: Now using the online exiftool {https://www.metadata2go.com/} or the exiftool command in kali view the metadata of the the_next_muggle_target.jpg

Step 4: You can view the comment : "Comment : Follow the serpents under the abbey...gloucester_cathedral"

Step 5: On combining these two part we get the flag as 

flagwars{severus_snape_gloucester_cathedral}

flag:
flagwars{severus_snape_gloucester_cathedral}
