CPP = c++
COMPILE_FLAGS = -Wall -Wextra -Werror -std=c++98 -pedantic -g -c
LINK_FLAGS =
NAME = hw

SRCS = main.cpp

OBJS = $(SRCS:.cpp=.o)

$(NAME): $(OBJS)
	$(CPP) $(LINK_FLAGS) -o $@ $^

all: $(NAME)

%.o: %.cpp
	$(CPP) $(COMPILE_FLAGS) $^ -o $@

clean:
	rm -f $(OBJS)

fclean: clean
	rm -f $(NAME)

re: fclean all

test: $(NAME) format-check
	valgrind --leak-check=full --show-leak-kinds=all ./$(NAME)

LINTERS_F = linters

format-fix:
	@bash ${LINTERS_F}/clang_format.sh fix .

format-check:
	@bash ${LINTERS_F}/clang_format.sh check .

.PHONY: all clean fclean re test format-fix format-check
