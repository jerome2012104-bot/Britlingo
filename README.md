/*
 * Project: YouTube AdBlock Logic Engine
 * Platform: Cross-Platform (Works on iPad/Programiz PRO)
 * Author: YourName
 * Description: A lightweight C++ engine to simulate URL filtering for YouTube Ads.
 */

#include <iostream>
#include <vector>
#include <string>

using namespace std;

class AdBlockEngine {
private:
    vector<string> blacklist = {
        "doubleclick.net", "googleads", "ads-atv.youtube", "pagead"
    };

public:
    void runFilter(string url) {
        bool blocked = false;
        for (const string& ad : blacklist) {
            if (url.find(ad) != string::npos) {
                blocked = true;
                break;
            }
        }
        cout << (blocked ? "[BLOCK] " : "[ALLOW] ") << url << endl;
    }
};

int main() {
    AdBlockEngine engine;
    cout << "YouTube AdBlock Engine initialized..." << endl;
    
    // Example URLs
    engine.runFilter("https://ads.youtube.com");
    engine.runFilter("https://youtube.com");
    
    return 0;
}
