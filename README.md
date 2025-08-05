#!/bin/bash

# Colors for text styling
RED='\033[0;31m'
GREEN='\033[0;32m'
BLUE='\033[0;34m'
PURPLE='\033[0;35m'
YELLOW='\033[0;33m'
CYAN='\033[0;36m'
BOLD='\033[1m'
RESET='\033[0m'

# Input data (from user's message)
CURRENT_DATE="2025-08-05 11:23:22"
USER="Nyxro0t"

# Extract date components
YEAR=$(echo $CURRENT_DATE | cut -d' ' -f1 | cut -d'-' -f1)
MONTH=$(echo $CURRENT_DATE | cut -d' ' -f1 | cut -d'-' -f2)
DAY=$(echo $CURRENT_DATE | cut -d' ' -f1 | cut -d'-' -f3)
TIME=$(echo $CURRENT_DATE | cut -d' ' -f2)
HOUR=$(echo $TIME | cut -d':' -f1)

# Function to show text with typing effect
type_text() {
    local text="$1"
    local color="$2"
    echo -ne "${color}"
    for (( i=0; i<${#text}; i++ )); do
        echo -n "${text:$i:1}"
        sleep 0.015
    done
    echo -e "${RESET}"
    sleep 0.3
}

# Function to generate replies based on different categories
generate_replies() {
    # Determine greeting based on time
    if (( HOUR >= 5 && HOUR < 12 )); then
        greeting="Good morning"
    elif (( HOUR >= 12 && HOUR < 17 )); then
        greeting="Good afternoon"
    elif (( HOUR >= 17 && HOUR < 22 )); then
        greeting="Good evening"
    else
        greeting="Hello night owl"
    fi
    
    # English formal replies
    type_text "FORMAL ENGLISH REPLIES:" "${BOLD}${BLUE}"
    type_text "1. ${greeting}, $USER. Your message was received at $CURRENT_DATE UTC." "${GREEN}"
    type_text "2. Thank you for your communication dated $CURRENT_DATE. We will process your request promptly." "${GREEN}"
    type_text "3. Dear $USER, we acknowledge receipt of your message. Reference: UTC-$CURRENT_DATE." "${GREEN}"
    type_text "4. Your timestamp of $CURRENT_DATE has been logged in our system with 500000 other entries." "${GREEN}"
    type_text "5. User $USER identified. Time synchronization confirmed at $CURRENT_DATE." "${GREEN}"
    echo
    
    # English casual replies
    type_text "CASUAL ENGLISH REPLIES:" "${BOLD}${BLUE}"
    type_text "1. Hey $USER! Got your message just now at $TIME. What's up?" "${YELLOW}"
    type_text "2. $USER! Haven't heard from you since... well, $CURRENT_DATE actually. 😄" "${YELLOW}"
    type_text "3. Yo! Message received at $TIME. There are 500000 reasons to reply to you, but I'll keep it short." "${YELLOW}"
    type_text "4. $USER is in the building! Timestamp: $CURRENT_DATE. Let's chat!" "${YELLOW}"
    type_text "5. Hey there! Your message arrived faster than 500000 others in the queue!" "${YELLOW}"
    echo
    
    # Nepali replies
    type_text "NEPALI REPLIES:" "${BOLD}${BLUE}"
    type_text "1. नमस्ते $USER! तपाईंको सन्देश $CURRENT_DATE मा प्राप्त भयो।" "${PURPLE}"
    type_text "   (Hello $USER! Your message was received on $CURRENT_DATE.)" "${CYAN}"
    type_text "2. धन्यवाद $USER। ५००००० सन्देशहरू मध्ये तपाईंको सन्देश हामीले पढ्यौं।" "${PURPLE}"
    type_text "   (Thank you $USER. We read your message among 500000 messages.)" "${CYAN}"
    type_text "3. तपाईंले पठाउनुभएको समय ($TIME) मा हामी तपाईंको जवाफ दिन तयार छौं।" "${PURPLE}"
    type_text "   (We are ready to answer you at the time you sent ($TIME).)" "${CYAN}"
    echo
    
    # Hindi replies
    type_text "HINDI REPLIES:" "${BOLD}${BLUE}"
    type_text "1. नमस्ते $USER! आपका संदेश $CURRENT_DATE पर प्राप्त हुआ।" "${RED}"
    type_text "   (Hello $USER! Your message was received on $CURRENT_DATE.)" "${CYAN}"
    type_text "2. धन्यवाद $USER। ५००००० संदेशों में से आपका संदेश हमने पढ़ा है।" "${RED}"
    type_text "   (Thank you $USER. We read your message among 500000 messages.)" "${CYAN}"
    type_text "3. आपके द्वारा भेजे गए समय ($TIME) पर हम आपको जवाब देने के लिए तैयार हैं।" "${RED}"
    type_text "   (We are ready to answer you at the time you sent ($TIME).)" "${CYAN}"
    echo
    
    # Humorous replies
    type_text "HUMOROUS REPLIES:" "${BOLD}${BLUE}"
    type_text "1. Alert! Alert! Message from $USER detected at precisely $CURRENT_DATE. This is not a drill!" "${GREEN}"
    type_text "2. Breaking news: $USER has been spotted sending messages at $TIME. More at 11." "${GREEN}"
    type_text "3. Your message traveled through 500000 servers to reach us. It's exhausted, please be gentle." "${GREEN}"
    type_text "4. Congratulations $USER! Your message from $CURRENT_DATE has won our 'Most Punctual Message' award." "${GREEN}"
    type_text "5. Time traveler detected: $USER somehow sent this message from $YEAR, which is suspiciously in the future!" "${GREEN}"
    echo
    
    # Love-themed replies (keeping the theme from previous script)
    type_text "LOVE-THEMED REPLIES:" "${BOLD}${BLUE}"
    type_text "1. Your message at $CURRENT_DATE was like one of 500000 stars lighting up our sky." "${PURPLE}"
    type_text "2. Dear $USER, even if we received 500000 messages, yours would stand out like a rose in a field." "${PURPLE}"
    type_text "3. The timestamp $TIME will forever be in our hearts, just like your username $USER." "${PURPLE}"
    type_text "4. If we had to choose one message out of 500000 to reply to, it would be yours, $USER." "${PURPLE}"
    type_text "5. Like the date $CURRENT_DATE, our appreciation for you is precisely measured and absolutely certain." "${PURPLE}"
    echo
}

# Main program
clear
echo -e "${BOLD}${CYAN}======================================================${RESET}"
echo -e "${BOLD}${CYAN}    500000 Personalized Replies Generator              ${RESET}"
echo -e "${BOLD}${CYAN}    Responding to: ${GREEN}$USER${CYAN} at ${YELLOW}$CURRENT_DATE    ${RESET}"
echo -e "${BOLD}${CYAN}======================================================${RESET}"
echo

type_text "Analyzing incoming message..." "${YELLOW}"
sleep 1
type_text "User identified: $USER" "${GREEN}"
type_text "Timestamp verified: $CURRENT_DATE UTC" "${GREEN}"
type_text "Generating 500000 potential replies..." "${YELLOW}"
echo

# Progress bar simulation
echo -ne "${YELLOW}Processing: [${RESET}"
for i in {1..30}; do
    echo -ne "${GREEN}#${RESET}"
    sleep 0.05
done
echo -e "${YELLOW}] Complete!${RESET}"
echo

type_text "Selecting optimal response categories from 500000 possibilities:" "${CYAN}"
sleep 1

# Generate the actual replies
generate_replies

# Conclusion
echo -e "${BOLD}${CYAN}======================================================${RESET}"
type_text "Reply generation complete! 500000 potential responses filtered to the most relevant." "${GREEN}"
type_text "Thank you for your message, $USER. We hope one of these 500000 reply styles meets your needs." "${GREEN}"
type_text "Connection timestamp: $CURRENT_DATE" "${YELLOW}"
echo -e "${BOLD}${CYAN}======================================================${RESET}"
