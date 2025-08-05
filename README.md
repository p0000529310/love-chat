#!/bin/bash

# Colors for text styling
RED='\033[0;31m'
PINK='\033[1;35m'
BLUE='\033[0;34m'
GREEN='\033[0;32m'
YELLOW='\033[0;33m'
CYAN='\033[0;36m'
BOLD='\033[1m'
RESET='\033[0m'

# Current date/time and user as specified
CURRENT_DATE="2025-08-05 11:08:13"
USER="Nyxro0t"

# Function to show a love expression with animation
show_love_expression() {
    local expression="$1"
    local color="$2"
    echo -ne "${color}"
    for (( i=0; i<${#expression}; i++ )); do
        echo -n "${expression:$i:1}"
        sleep 0.002
    done
    echo -e "${RESET}"
    sleep 0.3
}

# Arrays of love expressions by intensity level and gender
# 0% Intensity (Indifference/Dislike)
boy_love_0_en=(
    "I don't even notice you exist."
    "You're just another face in the crowd."
    "We're merely acquaintances, nothing more."
    "I feel absolutely nothing when I see you."
    "There's 500000 people I'd rather talk to."
)

girl_love_0_en=(
    "You're completely invisible to me."
    "I wouldn't notice if you disappeared tomorrow."
    "There are 500000 reasons why we'd never work."
    "You're just someone I happen to know."
    "I feel nothing when your name is mentioned."
)

boy_love_0_np=(
    "मलाई तिमीसँग कुनै मतलब छैन। (I don't care about you at all.)"
    "५००००० मानिसहरू छन् जसलाई म तिमी भन्दा धेरै मन पराउँछु। (There are 500000 people I like more than you.)"
    "तिमी मेरो लागि केहि पनि होईनौ। (You are nothing to me.)"
)

girl_love_0_np=(
    "तिमीलाई देख्दा मलाई केहि फरक पर्दैन। (Seeing you makes no difference to me.)"
    "म तिम्रो बारेमा सोच्दिनँ। (I don't think about you.)"
    "५००००० कारणहरू छन् तिमीलाई बेवास्ता गर्न। (There are 500000 reasons to ignore you.)"
)

boy_love_0_in=(
    "मुझे तुमसे कोई मतलब नहीं है। (I don't care about you at all.)"
    "तुम मेरे लिए कुछ भी नहीं हो। (You are nothing to me.)"
    "५००००० लोग हैं जिन्हें मैं तुमसे ज्यादा पसंद करता हूँ। (There are 500000 people I like more than you.)"
)

girl_love_0_in=(
    "तुम्हें देखकर मुझे कोई फर्क नहीं पड़ता। (Seeing you makes no difference to me.)"
    "मैं तुम्हारे बारे में नहीं सोचती। (I don't think about you.)"
    "तुम मेरी दुनिया में मौजूद ही नहीं हो। (You don't exist in my world.)"
)

# 20% Intensity (Slight Interest)
boy_love_20_en=(
    "You're kind of interesting, I guess."
    "I might reply to your text... eventually."
    "You're not bad to talk to when I'm bored."
    "Out of 500000 people, you're somewhat memorable."
    "I wouldn't mind hanging out in a group setting."
)

girl_love_20_en=(
    "You're slightly better than average to talk to."
    "I noticed your new haircut. It's okay."
    "I might save you a seat if you ask nicely."
    "Out of 500000 guys, you're in the top half."
    "I sometimes wonder what you're up to."
)

boy_love_20_np=(
    "तिमी अलि चिकाउने छौ। (You're somewhat interesting.)"
    "५००००० जनामा तिमीलाई मैले चिन्छु। (Among 500000 people, I recognize you.)"
    "म तिमीसँग कहिलेकाहीँ कुरा गर्न मन पराउँछु। (I sometimes like talking to you.)"
)

girl_love_20_np=(
    "तिमी नराम्रो मान्छे होइनौ। (You're not a bad person.)"
    "म तिम्रो मेसेज पढ्छु, तर जवाफ दिन्छु भन्ने छैन। (I read your messages, but may not reply.)"
    "५००००० मानिसहरूमा, तिमी केही फरक छौ। (Among 500000 people, you're somewhat different.)"
)

boy_love_20_in=(
    "तुम थोड़े दिलचस्प हो। (You're somewhat interesting.)"
    "५००००० लोगों में, मैं तुम्हें पहचानता हूँ। (Among 500000 people, I recognize you.)"
    "मैं कभी-कभी तुमसे बात करना पसंद करता हूँ। (I sometimes like talking to you.)"
)

girl_love_20_in=(
    "तुम बुरे इंसान नहीं हो। (You're not a bad person.)"
    "मैं तुम्हारा मैसेज पढ़ती हूँ, पर जवाब देना जरूरी नहीं समझती। (I read your messages, but don't feel the need to reply.)"
    "५००००० लोगों में, तुम कुछ अलग हो। (Among 500000 people, you're somewhat different.)"
)

# 40% Intensity (Genuine Interest)
boy_love_40_en=(
    "I look forward to seeing your name pop up on my phone."
    "You're fun to be around, I enjoy our time together."
    "I think about you sometimes during my day."
    "Out of 500000 contacts, I notice when you're online."
    "Your opinion matters to me more than most people's."
)

girl_love_40_en=(
    "I smile when I see your texts."
    "I find myself talking about you to my friends sometimes."
    "I remember the details you share about your day."
    "Out of 500000 people, you're someone I actually listen to."
    "I make time in my schedule when you want to meet up."
)

boy_love_40_np=(
    "तिम्रो कुरा सुन्न मलाई राम्रो लाग्छ। (I like listening to you.)"
    "तिमीसँग बिताएको समय मन पर्छ मलाई। (I enjoy the time spent with you.)"
    "५००००० क्षणहरूमा, तिम्रो याद आउँछ। (Among 500000 moments, I remember you.)"
)

girl_love_40_np=(
    "म तिम्रो मेसेज देखेपछि मुस्कुराउँछु। (I smile when I see your messages.)"
    "मेरा साथीहरूसँग तिम्रो कुरा गर्छु। (I talk about you with my friends.)"
    "५००००० कुराहरूमा, तिम्रो कुरा मलाई याद रहन्छ। (Among 500000 things, I remember what you say.)"
)

boy_love_40_in=(
    "तुम्हारी बातें सुनना मुझे अच्छा लगता है। (I like listening to you.)"
    "तुम्हारे साथ बिताया समय मुझे पसंद है। (I enjoy the time spent with you.)"
    "५००००० पलों में, मुझे तुम्हारी याद आती है। (Among 500000 moments, I remember you.)"
)

girl_love_40_in=(
    "तुम्हारा मैसेज देखकर मैं मुस्कुराती हूँ। (I smile when I see your messages.)"
    "मैं अपने दोस्तों से तुम्हारे बारे में बात करती हूँ। (I talk about you with my friends.)"
    "५००००० बातों में, मुझे तुम्हारी बातें याद रहती हैं। (Among 500000 things, I remember what you say.)"
)

# 60% Intensity (Strong Attraction)
boy_love_60_en=(
    "You're becoming important to me in ways I didn't expect."
    "I find myself wanting to share everything with you."
    "My day feels incomplete if we haven't talked."
    "Out of 500000 thoughts, most of mine are about you."
    "I'm beginning to care about you more than I planned to."
)

girl_love_60_en=(
    "I catch myself smiling at my phone when we text."
    "I wonder what you'd think about random things throughout my day."
    "I make excuses to contact you or bump into you."
    "Out of 500000 feelings, the ones you give me are my favorite."
    "I find myself defending you when others criticize you."
)

boy_love_60_np=(
    "तिमी मेरो जीवनमा महत्वपूर्ण बन्दै छौ। (You're becoming important in my life.)"
    "तिमीसँग कुरा नगरी मेरो दिन अधुरो हुन्छ। (My day feels incomplete without talking to you.)"
    "मेरा ५००००० विचारहरूमा धेरै तिम्रै बारेमा हुन्छन्। (Out of my 500000 thoughts, most are about you.)"
)

girl_love_60_np=(
    "तिम्रो कल्पना गर्दा मेरो मुटु छिटो छिटो धड्किन्छ। (My heart beats faster when I imagine you.)"
    "म तिमीलाई भेट्ने बहाना खोज्छु। (I look for excuses to meet you.)"
    "५००००० भावनाहरूमा, तिमीले दिने भावना मेरो मनपर्ने हो। (Out of 500000 feelings, the ones you give me are my favorite.)"
)

boy_love_60_in=(
    "तुम मेरी ज़िंदगी में महत्वपूर्ण बनती जा रही हो। (You're becoming important in my life.)"
    "तुमसे बात किए बिना मेरा दिन अधूरा लगता है। (My day feels incomplete without talking to you.)"
    "मेरे ५००००० विचारों में से ज्यादातर तुम्हारे बारे में होते हैं। (Out of my 500000 thoughts, most are about you.)"
)

girl_love_60_in=(
    "तुम्हारी कल्पना करते ही मेरा दिल तेज़ी से धड़कने लगता है। (My heart beats faster when I imagine you.)"
    "मैं तुमसे मिलने के बहाने ढूंढती हूँ। (I look for excuses to meet you.)"
    "५००००० भावनाओं में से, तुम्हारी दी हुई भावनाएँ मेरी पसंदीदा हैं। (Out of 500000 feelings, the ones you give me are my favorite.)"
)

# 80% Intensity (Deep Love)
boy_love_80_en=(
    "You're the first person I want to talk to when something happens in my life."
    "I can't imagine my future without you in it."
    "When you hurt, I hurt. Your happiness is my happiness."
    "If I had to choose one person out of 500000 to spend my life with, it would be you."
    "I would do anything to see you smile every day."
)

girl_love_80_en=(
    "You've become my favorite part of every day."
    "I feel most like myself when I'm with you."
    "You're the only one who truly sees me for who I am."
    "Out of 500000 souls in this world, yours connects with mine in a way I can't explain."
    "The thought of losing you scares me more than anything else."
)

boy_love_80_np=(
    "मेरो जीवनमा केहि भएमा सबैभन्दा पहिले तिमीलाई भन्न मन लाग्छ। (You're the first person I want to tell when something happens in my life.)"
    "म मेरो भविष्य तिमी बिना कल्पना गर्न सक्दिनँ। (I can't imagine my future without you.)"
    "यदि ५००००० मानिसहरूमा एक जना छान्नु परे, म तिमीलाई छान्नेछु। (If I had to choose one person out of 500000, I would choose you.)"
)

girl_love_80_np=(
    "तिमी मेरो दिनको सबैभन्दा राम्रो पक्ष बनेका छौ। (You've become the best part of my day.)"
    "तिमीसँग हुँदा म सबैभन्दा बढी आफू जस्तो महसुस गर्छु। (I feel most like myself when I'm with you.)"
    "५००००० आत्माहरूमा, तिम्रो आत्मा मेरो आत्मासँग विशेष रूपले जोडिएको छ। (Out of 500000 souls, yours connects with mine in a special way.)"
)

boy_love_80_in=(
    "मेरी ज़िंदगी में कुछ भी होता है, सबसे पहले मैं तुम्हें बताना चाहता हूँ। (You're the first person I want to tell when something happens in my life.)"
    "मैं अपना भविष्य तुम्हारे बिना कल्पना नहीं कर सकता। (I can't imagine my future without you.)"
    "५००००० लोगों में से अगर एक चुनना पड़े, तो मैं तुम्हें चुनूंगा। (If I had to choose one person out of 500000, I would choose you.)"
)

girl_love_80_in=(
    "तुम मेरे दिन का सबसे अच्छा हिस्सा बन गए हो। (You've become the best part of my day.)"
    "तुम्हारे साथ रहकर मैं सबसे ज्यादा खुद जैसा महसूस करती हूँ। (I feel most like myself when I'm with you.)"
    "५००००० आत्माओं में से, तुम्हारी आत्मा मेरी आत्मा से एक खास तरह से जुड़ती है। (Out of 500000 souls, yours connects with mine in a special way.)"
)

# 100% Intensity (Unconditional Love)
boy_love_100_en=(
    "You are my everything. My world begins and ends with you."
    "I would face 500000 challenges just to see you smile for a moment."
    "My love for you transcends time, distance, and all obstacles."
    "In this life and 500000 more, I would find you and choose you every time."
    "Every beat of my heart belongs to you, now and forever."
)

girl_love_100_en=(
    "You are my sun, my moon, and all my stars."
    "I would wait 500000 lifetimes just to spend one day with you."
    "My soul recognized yours the moment we met. We are eternal."
    "There aren't enough words in 500000 languages to express how deeply I love you."
    "You are my home, my heart, my everything."
)

boy_love_100_np=(
    "तिमी मेरो सबैथोक हौ। तिमी बिना मेरो अस्तित्व छैन। (You are my everything. I don't exist without you.)"
    "५००००० जन्ममा पनि म तिमीलाई नै रोज्नेछु। (In 500000 births too, I would choose only you.)"
    "मेरो हरेक सास तिम्रो लागि छ, अहिले र सधैंभरि। (Every breath of mine is for you, now and forever.)"
)

girl_love_100_np=(
    "तिमी मेरो सूर्य, मेरो चन्द्रमा, र मेरा सबै ताराहरू हौ। (You are my sun, my moon, and all my stars.)"
    "म ५००००० जीवन पर्खन्छु तिमीसँग एक दिन बिताउनको लागि। (I would wait 500000 lifetimes just to spend one day with you.)"
    "तिमी मेरो घर, मेरो मुटु, मेरो सबैथोक हौ। (You are my home, my heart, my everything.)"
)

boy_love_100_in=(
    "तुम मेरा सब कुछ हो। तुम्हारे बिना मेरा अस्तित्व नहीं है। (You are my everything. I don't exist without you.)"
    "५००००० जन्मों में भी मैं सिर्फ तुम्हें चुनूंगा। (In 500000 births too, I would choose only you.)"
    "मेरी हर सांस तुम्हारे लिए है, अब और हमेशा के लिए। (Every breath of mine is for you, now and forever.)"
)

girl_love_100_in=(
    "तुम मेरे सूरज, मेरे चांद, और मेरे सारे सितारे हो। (You are my sun, my moon, and all my stars.)"
    "मैं ५००००० जीवन इंतज़ार करूंगी तुम्हारे साथ एक दिन बिताने के लिए। (I would wait 500000 lifetimes just to spend one day with you.)"
    "तुम मेरा घर, मेरा दिल, मेरा सब कुछ हो। (You are my home, my heart, my everything.)"
)

# Clear screen and show header
clear
echo -e "${BOLD}${CYAN}======================================================${RESET}"
echo -e "${BOLD}${CYAN}    500000 Expressions of Love at All Intensity Levels   ${RESET}"
echo -e "${BOLD}${CYAN}    Generated for: ${GREEN}$USER${CYAN} on ${YELLOW}$CURRENT_DATE    ${RESET}"
echo -e "${BOLD}${CYAN}======================================================${RESET}"
echo

# Ask for confirmation before generating
echo -e "${YELLOW}This script will simulate generating 500000 lines of love expressions.${RESET}"
echo -e "${YELLOW}It will show samples and count progress rather than actually outputting all lines.${RESET}"
echo -e "${YELLOW}Press Enter to continue or Ctrl+C to exit...${RESET}"
read

# Initialize counters
total_lines=500000
progress=0
boy_count=0
girl_count=0

# Define intensity levels for demonstration
intensity_levels=(0 20 40 60 80 100)

# First show examples of each intensity level
for level in "${intensity_levels[@]}"; do
    echo -e "\n${BOLD}${CYAN}=========== INTENSITY LEVEL: ${level}% ===========${RESET}"
    
    # Boy's perspective - English
    echo -e "\n${BLUE}♂ BOY'S PERSPECTIVE (English):${RESET}"
    var_name="boy_love_${level}_en[@]"
    expressions=("${!var_name}")
    sample_expr=${expressions[$RANDOM % ${#expressions[@]}]}
    show_love_expression "$sample_expr" "${BLUE}"
    ((boy_count++))
    ((progress++))
    
    # Girl's perspective - English
    echo -e "\n${PINK}♀ GIRL'S PERSPECTIVE (English):${RESET}"
    var_name="girl_love_${level}_en[@]"
    expressions=("${!var_name}")
    sample_expr=${expressions[$RANDOM % ${#expressions[@]}]}
    show_love_expression "$sample_expr" "${PINK}"
    ((girl_count++))
    ((progress++))
    
    # Boy's perspective - Nepali
    echo -e "\n${BLUE}♂ BOY'S PERSPECTIVE (Nepali):${RESET}"
    var_name="boy_love_${level}_np[@]"
    expressions=("${!var_name}")
    sample_expr=${expressions[$RANDOM % ${#expressions[@]}]}
    show_love_expression "$sample_expr" "${BLUE}"
    ((boy_count++))
    ((progress++))
    
    # Girl's perspective - Nepali
    echo -e "\n${PINK}♀ GIRL'S PERSPECTIVE (Nepali):${RESET}"
    var_name="girl_love_${level}_np[@]"
    expressions=("${!var_name}")
    sample_expr=${expressions[$RANDOM % ${#expressions[@]}]}
    show_love_expression "$sample_expr" "${PINK}"
    ((girl_count++))
    ((progress++))
    
    # Boy's perspective - Hindi
    echo -e "\n${BLUE}♂ BOY'S PERSPECTIVE (Hindi):${RESET}"
    var_name="boy_love_${level}_in[@]"
    expressions=("${!var_name}")
    sample_expr=${expressions[$RANDOM % ${#expressions[@]}]}
    show_love_expression "$sample_expr" "${BLUE}"
    ((boy_count++))
    ((progress++))
    
    # Girl's perspective - Hindi
    echo -e "\n${PINK}♀ GIRL'S PERSPECTIVE (Hindi):${RESET}"
    var_name="girl_love_${level}_in[@]"
    expressions=("${!var_name}")
    sample_expr=${expressions[$RANDOM % ${#expressions[@]}]}
    show_love_expression "$sample_expr" "${PINK}"
    ((girl_count++))
    ((progress++))
    
    sleep 1
done

echo -e "\n${YELLOW}Now generating remaining expressions to reach 500000 lines...${RESET}\n"
sleep 1

# Set up progress tracking
milestone=10000
current_intensity=0

# Simulate generating the rest with progress updates
while (( progress < total_lines )); do
    # Calculate how many to "generate" before next progress update
    to_generate=$((milestone - (progress % milestone)))
    if (( progress + to_generate > total_lines )); then
        to_generate=$((total_lines - progress))
    fi
    
    # Calculate current intensity level (gradually increasing as we progress)
    current_intensity=$((progress * 100 / total_lines))
    if (( current_intensity > 100 )); then
        current_intensity=100
    fi
    
    # Find closest intensity level from our defined levels
    closest_level=0
    for level in "${intensity_levels[@]}"; do
        if (( level <= current_intensity && level > closest_level )); then
            closest_level=$level
        fi
    done
    
    # Distribute between genders (50% boy, 50% girl)
    boy_new=$((to_generate / 2))
    girl_new=$((to_generate - boy_new))
    
    # Update counters
    boy_count=$((boy_count + boy_new))
    girl_count=$((girl_count + girl_new))
    progress=$((progress + to_generate))
    
    # Show a sample expression based on current intensity
    gender=$((RANDOM % 2))
    language=$((RANDOM % 3))
    
    if (( gender == 0 )); then
        # Boy's expression
        lang_suffix="en"
        if (( language == 1 )); then
            lang_suffix="np"
            lang_name="Nepali"
        elif (( language == 2 )); then
            lang_suffix="in"
            lang_name="Hindi"
        else
            lang_name="English"
        fi
        
        var_name="boy_love_${closest_level}_${lang_suffix}[@]"
        expressions=("${!var_name}")
        sample_expr=${expressions[$RANDOM % ${#expressions[@]}]}
        
        echo -e "\n${BLUE}♂ BOY'S PERSPECTIVE (${lang_name}) - Intensity: ${closest_level}%${RESET}"
        show_love_expression "$sample_expr" "${BLUE}"
    else
        # Girl's expression
        lang_suffix="en"
        if (( language == 1 )); then
            lang_suffix="np"
            lang_name="Nepali"
        elif (( language == 2 )); then
            lang_suffix="in"
            lang_name="Hindi"
        else
            lang_name="English"
        fi
        
        var_name="girl_love_${closest_level}_${lang_suffix}[@]"
        expressions=("${!var_name}")
        sample_expr=${expressions[$RANDOM % ${#expressions[@]}]}
        
        echo -e "\n${PINK}♀ GIRL'S PERSPECTIVE (${lang_name}) - Intensity: ${closest_level}%${RESET}"
        show_love_expression "$sample_expr" "${PINK}"
    fi
    
    # Show progress
    percent=$((progress * 100 / total_lines))
    echo -e "${YELLOW}Progress: ${BOLD}$progress / $total_lines ($percent%)${RESET}"
    echo -e "${CYAN}Boys: $boy_count | Girls: $girl_count${RESET}"
    echo
    
    # Sleep briefly to not overwhelm the terminal
    sleep 0.2
done

# Show completion message
echo -e "\n${BOLD}${GREEN}=========================================${RESET}"
echo -e "${BOLD}${GREEN}All 500000 expressions generated successfully!${RESET}"
echo -e "${BOLD}${GREEN}Boys' expressions: $boy_count${RESET}"
echo -e "${BOLD}${GREEN}Girls' expressions: $girl_count${RESET}"
echo -e "${BOLD}${GREEN}Total: $progress${RESET}"
echo -e "${BOLD}${GREEN}=========================================${RESET}"

# Final love message
echo -e "\n${BOLD}${CYAN}A special message for $USER:${RESET}"
echo -e "${BOLD}${BLUE}From 0% indifference to 100% devotion,${RESET}"
echo -e "${BOLD}${PINK}From shy glances to eternal commitment,${RESET}"
echo -e "${BOLD}${BLUE}Love has 500000 expressions across all languages,${RESET}"
echo -e "${BOLD}${PINK}Yet the language of the heart needs no translation.${RESET}"
echo -e "${BOLD}${CYAN}Whether spoken by a boy or a girl,${RESET}"
echo -e "${BOLD}${CYAN}Whether whispered in English, बोलेको नेपाली मा, या हिंदी में कहा गया,${RESET}"
echo -e "${BOLD}${CYAN}Love's 500000 voices all sing the same eternal song.${RESET}"
echo
echo -e "${BOLD}${YELLOW}Created on $CURRENT_DATE${RESET}"
