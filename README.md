#!/bin/bash
clear

# Cyber Security typewriter animation function
animate_text() {
    local text="$1"
    local delay=0.01
    for ((i=0; i<${#text}; i++)); do
        echo -n "${text:$i:1}"
        sleep $delay
    done
    echo ""
}

# Terminal color codes (Matrix/Cyber theme)
GREEN='\033[0;32m'
RED='\033[0;31m'
CYAN='\033[0;36m'
NC='\033[0m' # No Color

echo -e "${GREEN}================================================="
animate_text " [+] CYBER_EXTRACTOR // YT-DLP CORE ACTIVATED... "
echo -e "=================================================${NC}"
echo ""

echo -e -n "${CYAN}[?] Enter Target Video or Playlist URL: ${NC}"
read -r VIDEO_URL

if [ -z "$VIDEO_URL" ]; then
    echo -e "${RED}[!] Error: Target URL cannot be empty! Aborting...${NC}"
    exit 1
fi

echo ""
echo -e "${GREEN}[+] Select extraction payload quality:${NC}"
echo "-----------------------------------------"
echo "1. Best Resolution (Max Quality Available)"
echo "2. 1080p60 (Full HD @ 60fps)"
echo "3. 1080p (Full HD)"
echo "4. 720p60 (HD @ 60fps)"
echo "5. 720p (HD)"
echo "6. 480p (Medium Quality)"
echo "7. 360p (Low Quality)"
echo "8. 240p (Ultra Low Quality)"
echo "9. 144p (Minimum Data Quality)"
echo "10. Download Audio Only (Best MP3)"
echo "11. Download Audio Only (Best M4A)"
echo "12. Exit Secure Session"
echo "-----------------------------------------"
echo -e -n "${CYAN}[?] Enter your choice [1-12]: ${NC}"
read -r CHOICE

echo ""
echo -e "${GREEN}[*] Initializing bypass and download protocol...${NC}"
echo "-----------------------------------------"

# Expanded map based on image 1000039327.jpg while preserving yt-dlp syntax
case $CHOICE in
    1) yt-dlp -f "bestvideo+bestaudio/best" "$VIDEO_URL" ;;
    2) yt-dlp -f "bestvideo[height<=1080][fps>=60]+bestaudio/best[height<=1080]" "$VIDEO_URL" ;;
    3) yt-dlp -f "bestvideo[height<=1080]+bestaudio/best[height<=1080]" "$VIDEO_URL" ;;
    4) yt-dlp -f "bestvideo[height<=720][fps>=60]+bestaudio/best[height<=720]" "$VIDEO_URL" ;;
    5) yt-dlp -f "bestvideo[height<=720]+bestaudio/best[height<=720]" "$VIDEO_URL" ;;
    6) yt-dlp -f "bestvideo[height<=480]+bestaudio/best[height<=480]" "$VIDEO_URL" ;;
    7) yt-dlp -f "bestvideo[height<=360]+bestaudio/best[height<=360]" "$VIDEO_URL" ;;
    8) yt-dlp -f "bestvideo[height<=240]+bestaudio/best[height<=240]" "$VIDEO_URL" ;;
    9) yt-dlp -f "bestvideo[height<=144]+bestaudio/best[height<=144]" "$VIDEO_URL" ;;
   10) yt-dlp -x --audio-format mp3 --audio-quality 0 "$VIDEO_URL" ;;
   11) yt-dlp -f "ba[ext=m4a]" "$VIDEO_URL" ;;
   12) echo -e "${RED}[!] Exiting secure session.${NC}"; exit 0 ;;
    *) echo -e "${RED}[!] Invalid option! Hack prevented.${NC}"; exit 1 ;;
esac

echo ""
echo -e "${GREEN}================================================="
animate_text " [✓] SUCCESS: Data Extraction Completed! "
echo -e "=================================================${NC}"
