# JavaTMI
Java Library for the Twitch Messaging Interface based on https://github.com/blay09/JavaIRC

**Features**
* Simple, straight-forward API
* Event calls for various Twitch events, such as subscriptions or hosts
* No runtime dependencies on other libraries (apart from JavaIRC)
* Supports anonymous connections (read-only)
* Helper methods for the various Twitch commands

**Example Usage**
```java
import net.blay09.javatmi.TMIAdapter;
import net.blay09.javatmi.TMIClient;
import net.blay09.javatmi.TwitchUser;

public class JavaTMIExample extends TMIAdapter {

    @Override
    void onResubscribe(TMIClient client, String channel, TwitchUser user, int months, String message) {
        client.send(channel, "Welcome back, " + user.getDisplayName() + "! Thank you for " + months + " months of support. <3");
    }

    public static void main(String[] args) {
        TMIClient client = new TMIClient("blay09", "oauth:1234567890abcdefghijklmn", Collections.singletonList("#blay09"), new JavaTMIExample());
        client.connect();
    }
}
```