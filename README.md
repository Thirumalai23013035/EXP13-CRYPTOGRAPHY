# Ex - 13 - MESSAGE AUTHENTICATION CODE(MAC)

```
Name: THIRUMALAI V
Register No : 212223040229
```

## Aim:
To implement a Message Authentication Code (MAC) using a cryptographic hash function to ensure data integrity and authenticity.



## ALGORITHM:

#### **Step 01:**
* Receive the message M and the secret key K known to both the sender and receiver.

#### **Step 02:** 
* Choose a secure hash function, such as SHA-256, to ensure strong integrity.

#### **Step 03:** Combine Key and Message:
* Use HMAC to combine the key K with the message M securely.

#### **Step 04:** 
* Generate the MAC by applying the HMAC function to the combined key and message.

#### **Step 05:** 
* Output the generated MAC value that will accompany the message for verification.

#### **Step 06:** 
* On the receiver's side, recompute the MAC and compare it with the received MAC to check authenticity.

#### **Step 07:** 
* On the receiver's side, recompute the MAC and compare it with the received MAC to check authenticity.

##  PROGRAM:

```
exp 13
#include <stdio.h>
#include <string.h>

#define MAC_SIZE 32 // Define MAC size in bytes

// Function to compute a simple MAC using XOR
void computeMAC(const char *key, const char *message, char *mac) {
    int key_len = strlen(key);
    int msg_len = strlen(message);

    // XOR the key and message, repeating if necessary
    for (int i = 0; i < MAC_SIZE; i++) {
        mac[i] = key[i % key_len] ^ message[i % msg_len]; // Simple XOR operation
    }
    mac[MAC_SIZE] = '\0'; // Null-terminate the MAC string
}

int main() {
    char key[100], message[100];
    char mac[MAC_SIZE + 1]; // Buffer for MAC (+1 for null terminator)
    char receivedMAC[MAC_SIZE + 1]; // Buffer for input of received MAC

    // Step 1: Input secret key
    printf("Enter the secret key: ");
    scanf("%s", key);

    // Step 2: Input the message
    printf("Enter the message: ");
    scanf("%s", message);

    // Step 3: Compute the MAC
    computeMAC(key, message, mac);

    // Step 4: Display the computed MAC in hexadecimal
    printf("Computed MAC (in hex): ");
    for (int i = 0; i < MAC_SIZE; i++) {
        printf("%02x", (unsigned char)mac[i]); // Print each byte as hex
    }
    printf("\n");

    // Step 5: Input the received MAC (for verification)
    printf("Enter the received MAC (as hex): ");
    for (int i = 0; i < MAC_SIZE; i++) {
        scanf("%2hhx", &receivedMAC[i]);
    }

    // Compare the computed MAC with the received MAC
    if (memcmp(mac, receivedMAC, MAC_SIZE) == 0) {
        printf("MAC verification successful. Message is authentic.\n");
    } else {
        printf("MAC verification failed. Message is not authentic.\n");
    }

    return 0;
}
```

## OUTPUT:
![Screenshot 2024-11-11 083602](https://github.com/user-attachments/assets/0bc2d9f6-add5-4cd3-98fe-e986ccfa959f)


## RESULT:
Hence, to implement a Message Authentication Code (MAC) using a cryptographic hash function ensures data integrity and authenticity for secure communications.
