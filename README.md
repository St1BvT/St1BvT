def find_words_in_phrases(phrases, words_to_find):
    result = {}
    
    for word in words_to_find:
        result[word] = {}

        for phrase in phrases:
            positions = []

            start = 0
            while start < len(phrase):
                position = phrase.find(word, start)
                if position != -1:
                    positions.append(position)
                    start = position + 1
                else:
                    break

            if positions:
                result[word][phrase] = positions
            
    return result

# Nhập cụm từ từ người dùng
phrases_input = input("Nhập cụm từ, ngăn cách bằng dấu phẩy: ")
phrases = [phrase.strip() for phrase in phrases_input.split(',')]

# Nhập từ cần tìm
words_input = input("Nhập các từ cần tìm, ngăn cách bằng dấu phẩy: ")
words_to_find = [word.strip() for word in words_input.split(',')]

# Tìm vị trí của từ cần tìm trong các cụm từ
word_positions = find_words_in_phrases(phrases, words_to_find)

# In kết quả ra màn hình
for word, result in word_positions.items():
    if result:
        print(f"Từ '{word}' tìm thấy trong các cụm từ sau:")
        for phrase, positions in result.items():
            print(f"  - Trong cụm từ '{phrase}' tại vị trí {', '.join(str(pos) for pos in positions)}")
    else:
        print(f"Từ '{word}' không tìm thấy trong các cụm từ")
