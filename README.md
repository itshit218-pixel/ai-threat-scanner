# AI Threat Scanner
# Detects harmful AI tools and websites

import urllib.request

HARMFUL_SITES = [
    "deepfakeai.com",
    "stealbot.net",
    "malwareai.com",
    "phishingai.net",
    "darkwebai.com",
    "spywarebot.com",
    "ransomwareai.net",
    "fraudai.com"
]

SUSPICIOUS_KEYWORDS = [
    "deepfake",
    "crack",
    "hack",
    "steal",
    "phish",
    "ransomware",
    "malware",
    "spyware",
    "fraud",
    "illegal"
]

def check_url(url):
    url = url.lower().strip()
    
    # Check against known harmful sites
    for site in HARMFUL_SITES:
        if site in url:
            return "DANGEROUS", f"Known harmful AI site detected: {site}"
    
    # Check for suspicious keywords
    for keyword in SUSPICIOUS_KEYWORDS:
        if keyword in url:
            return "SUSPICIOUS", f"Suspicious keyword found: {keyword}"
    
    return "SAFE", "No threats detected"

def generate_report(url, status, reason):
    print("\n" + "="*40)
    print("   AI THREAT SCANNER REPORT")
    print("="*40)
    print(f"URL Scanned  : {url}")
    print(f"Threat Level : {status}")
    print(f"Reason       : {reason}")
    print("="*40)
    
    if status == "DANGEROUS":
        print("ACTION: Block this site immediately!")
    elif status == "SUSPICIOUS":
        print("ACTION: Proceed with caution.")
    else:
        print("ACTION: Safe to use.")
    print("="*40 + "\n")

def main():
    print("\nWelcome to AI Threat Scanner")
    print("Protecting you from harmful AI tools\n")
    
    while True:
        url = input("Enter website URL to scan (or 'quit' to exit): ")
        if url.lower() == 'quit':
            print("Thank you for using AI Threat Scanner. Stay safe!")
            break
        
        status, reason = check_url(url)
        generate_report(url, status, reason)

if __name__ == "__main__":
    main()
