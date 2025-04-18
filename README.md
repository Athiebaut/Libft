<p>LibftYour very first own librarySummary:This project involves coding a C library that will include numerous general purposefunctions for your programs.Version: 16.7ContentsIIntroduction2IICommon Instructions3IIIMandatory part5III.1Technical considerations . . . . . . . . . . . . . . . . . . . . . . . . . .5III.2Part 1 - Libc functions. . . . . . . . . . . . . . . . . . . . . . . . . .6III.3Part 2 - Additional functions . . . . . . . . . . . . . . . . . . . . . . .7IVBonus part11VSubmission and peer-evaluation151Chapter IIntroductionC programming can be quite tedious without access to the highly useful standard func-tions. This project aims to help you understand how these functions work by implement-ing them yourself and learning to use them effectively. You will create your own library,which will be valuable for your future C school assignments.Take the time to expand your libft throughout the year. However, when working on anew project, always check that the functions used in your library comply with the projectguidelines.2Chapter IICommon Instructions• Your project must be written in C.• Your project must be written in accordance with the Norm. If you have bonusfiles/functions, they are included in the norm check, and you will receive a 0 ifthere is a norm error.• Your functions should not quit unexpectedly (segmentation fault, bus error, dou-ble free, etc.) except for undefined behavior. If this occurs, your project will beconsidered non-functional and will receive a 0 during the evaluation.• All heap-allocated memory must be properly freed when necessary. Memory leakswill not be tolerated.• If the subject requires it, you must submit a Makefile that compiles your sourcefiles to the required output with the flags -Wall, -Wextra, and -Werror, using cc.Additionally, your Makefile must not perform unnecessary relinking.• Your Makefile must at contain at least the rules $(NAME), all, clean, fclean andre.• To submit bonuses for your project, you must include a bonus rule in your Makefile,which will add all the various headers, libraries, or functions that are not allowed inthe main part of the project. Bonuses must be placed in <em>bonus.{c/h} files, unlessthe subject specifies otherwise. The evaluation of mandatory and bonus parts isconducted separately.• If your project allows you to use your libft, you must copy its sources and itsassociated Makefile into a libft folder. Your project’s Makefile must compilethe library by using its Makefile, then compile the project.• We encourage you to create test programs for your project, even though this workdoes not need to be submitted and will not be graded. It will give you anopportunity to easily test your work and your peers’ work. You will find these testsespecially useful during your defence. Indeed, during defence, you are free to useyour tests and/or the tests of the peer you are evaluating.• Submit your work to the assigned Git repository. Only the work in the Git repos-itory will be graded. If Deepthought is assigned to grade your work, it will occur3LibftYour very first own libraryafter your peer-evaluations. If an error happens in any section of your work duringDeepthought’s grading, the evaluation will stop.4Chapter IIIMandatory partProgram namelibft.aTurn in filesMakefile, libft.h, ft</em><em>.cMakefileNAME, all, clean, fclean, reExternal functs.Detailed belowLibft authorizedn/aDescriptionCreate your own library:a collection of functionsthat will serve as a useful tool throughout yourcursus.III.1Technical considerations• Declaring global variables is strictly forbidden.• If you need helper functions to break down a more complex function, define themas static functions to restrict their scope to the appropriate file.• All files must be placed at the root of your repository.• Submitting unused files is not allowed.• Every .c file must compile with the following flags: -Wall -Wextra -Werror.• You must use the ar command to create your library. The use of libtool is strictlyforbidden.• Your libft.a must be created at the root of your repository.5LibftYour very first own libraryIII.2Part 1 - Libc functionsTo begin, you must reimplement a set of functions from the libc. Your version will havethe same prototypes and behaviors as the originals, adhering strictly to their definitionsin the man page. The only difference will be their names, as they must start with the’ft_’ prefix. For example, strlen becomes ft_strlen.Some of the function prototypes you need to reimplement use the’restrict’ qualifier.This keyword is part of the C99 standard.Therefore, it is forbidden to include it in your own prototypes or tocompile your code with the -std=c99 flag.The following functions must be rewritten without relying on external functions:• isalpha• isdigit• isalnum• isascii• isprint• strlen• memset• bzero• memcpy• memmove• strlcpy• strlcat• toupper• tolower• strchr• strrchr• strncmp• memchr• memcmp• strnstr• atoiTo implement the two following functions, you will use malloc():• calloc• strdupDepending on your current operating system, the ’calloc’ function’sbehavior may differ from its man page description.Follow thisrule instead:If nmemb or size is 0, then calloc() returns a uniquepointer value that can be successfully passed to free().6LibftYour very first own libraryIII.3Part 2 - Additional functionsIn this second part, you must develop a set of functions that are either not included inthe libc, or exist in a different form.Some of the functions from Part 1 may be useful for implementing thefunctions below.Function nameft_substrPrototypechar *ft_substr(char const *s, unsigned int start,size_t len);Turn in files-Parameterss:The original string from which to create thesubstring.start:The starting index of the substring within’s’.len:The maximum length of the substring.Return valueThe substring.NULL if the allocation fails.External functs.mallocDescriptionAllocates memory (using malloc(3)) and returns asubstring from the string ’s’.The substring starts at index ’start’ and has amaximum length of ’len’.Function nameft_strjoinPrototypechar *ft_strjoin(char const *s1, char const *s2);Turn in files-Parameterss1:The prefix string.s2:The suffix string.Return valueThe new string.NULL if the allocation fails.External functs.mallocDescriptionAllocates memory (using malloc(3)) and returns anew string, which is the result of concatenating’s1’ and ’s2’.7LibftYour very first own libraryFunction nameft_strtrimPrototypechar *ft_strtrim(char const *s1, char const *set);Turn in files-Parameterss1:The string to be trimmed.set:The string containing the set of charactersto be removed.Return valueThe trimmed string.NULL if the allocation fails.External functs.mallocDescriptionAllocates memory (using malloc(3)) and returns acopy of ’s1’ with characters from ’set’ removedfrom the beginning and the end.Function nameft_splitPrototypechar *</em>ft<em>split(char const *s, char c);Turn in files-Parameterss:The string to be split.c:The delimiter character.Return valueThe array of new strings resulting from the split.NULL if the allocation fails.External functs.malloc, freeDescriptionAllocates memory (using malloc(3)) and returns anarray of strings obtained by splitting ’s’ usingthe character ’c’ as a delimiter.The array mustend with a NULL pointer.Function nameft</em>itoaPrototypechar <em>ft_itoa(int n);Turn in files-Parametersn:The integer to convert.Return valueThe string representing the integer.NULL if the allocation fails.External functs.mallocDescriptionAllocates memory (using malloc(3)) and returnsa string representing the integer received as anargument.Negative numbers must be handled.8LibftYour very first own libraryFunction nameft_strmapiPrototypechar *ft_strmapi(char const *s, char (</em>f)(unsignedint, char));Turn in files-Parameterss:The string to iterate over.f:The function to apply to each character.Return valueThe string created from the successive applicationsof ’f’.Returns NULL if the allocation fails.External functs.mallocDescriptionApplies the function f to each character of thestring s, passing its index as the first argumentand the character itself as the second.A newstring is created (using malloc(3)) to store theresults from the successive applications of f.Function nameft<em>striteriPrototypevoid ft</em>striteri(char <em>s, void (</em>f)(unsigned int,char<em>));Turn in files-Parameterss:The string to iterate over.f:The function to apply to each character.Return valueNoneExternal functs.NoneDescriptionApplies the function ’f’ to each character of thestring passed as argument, passing its index asthe first argument.Each character is passed byaddress to ’f’ so it can be modified if necessary.Function nameft_putchar_fdPrototypevoid ft_putchar_fd(char c, int fd);Turn in files-Parametersc:The character to output.fd:The file descriptor on which to write.Return valueNoneExternal functs.writeDescriptionOutputs the character ’c’ to the specified filedescriptor.9LibftYour very first own libraryFunction nameft_putstr_fdPrototypevoid ft_putstr_fd(char *s, int fd);Turn in files-Parameterss:The string to output.fd:The file descriptor on which to write.Return valueNoneExternal functs.writeDescriptionOutputs the string ’s’ to the specified filedescriptor.Function nameft_putendl_fdPrototypevoid ft_putendl_fd(char *s, int fd);Turn in files-Parameterss:The string to output.fd:The file descriptor on which to write.Return valueNoneExternal functs.writeDescriptionOutputs the string ’s’ to the specified filedescriptor followed by a newline.Function nameft_putnbr_fdPrototypevoid ft_putnbr_fd(int n, int fd);Turn in files-Parametersn:The integer to output.fd:The file descriptor on which to write.Return valueNoneExternal functs.writeDescriptionOutputs the integer ’n’ to the specified filedescriptor.10Chapter IVBonus partOnce you have completed the mandatory part, consider taking on this extra challenge.Successfully completing this section will earn you bonus points.Memory and string manipulation functions are useful. But you will soon discover thatmanipulating lists is even more useful.You have to use the following structure to represent a node of your list. Add its declara-tion to your libft.h file:typedef structs_list{void</em>content;struct s<em>list*next;}t</em>list;The members of the t<em>list struct are:• content: The data contained in the node.Using void * allows you to store any type of data.• next: The address of the next node, or NULL if the next node is the last one.In your Makefile, add a make bonus rule to add the bonus functions in your libft.a.The bonus part will only be evaluated if the mandatory part isperfect."Perfect" means the mandatory functions are implementedcorrectly and work without issues.If you fail to meet ALL themandatory requirements, the bonus part will not be considered at all.11LibftYour very first own libraryImplement the following functions in order to easily use your lists.Function nameft</em>lstnewPrototypet<em>list *ft</em>lstnew(void <em>content);Turn in files-Parameterscontent:The content to store in the new node.Return valueA pointer to the new nodeExternal functs.mallocDescriptionAllocates memory (using malloc(3)) and returnsa new node.The ’content’ member variable isinitialized with the given parameter ’content’.The variable ’next’ is initialized to NULL.Function nameft_lstadd_frontPrototypevoid ft_lstadd_front(t_list *</em>lst, t<em>list *new);Turn in files-Parameterslst:The address of a pointer to the first node ofa list.new:The address of a pointer to the node to beadded.Return valueNoneExternal functs.NoneDescriptionAdds the node ’new’ at the beginning of the list.Function nameft</em>lstsizePrototypeint ft<em>lstsize(t</em>list <em>lst);Turn in files-Parameterslst:The beginning of the list.Return valueThe length of the listExternal functs.NoneDescriptionCounts the number of nodes in the list.Function nameft_lstlastPrototypet_list *ft_lstlast(t_list *lst);Turn in files-Parameterslst:The beginning of the list.Return valueLast node of the listExternal functs.NoneDescriptionReturns the last node of the list.12LibftYour very first own libraryFunction nameft_lstadd_backPrototypevoid ft_lstadd_back(t_list *</em>lst, t<em>list *new);Turn in files-Parameterslst:The address of a pointer to the first node ofa list.new:The address of a pointer to the node to beadded.Return valueNoneExternal functs.NoneDescriptionAdds the node ’new’ at the end of the list.Function nameft</em>lstdelonePrototypevoid ft<em>lstdelone(t</em>list <em>lst, void (</em>del)(void<em>));Turn in files-Parameterslst:The node to free.del:The address of the function used to deletethe content.Return valueNoneExternal functs.freeDescriptionTakes a node as parameter and frees its contentusing the function ’del’.Free the node itself butdoes NOT free the next node.Function nameft_lstclearPrototypevoid ft_lstclear(t_list *</em>lst, void (<em>del)(void</em>));Turn in files-Parameterslst:The address of a pointer to a node.del:The address of the function used to deletethe content of the node.Return valueNoneExternal functs.freeDescriptionDeletes and frees the given node and all itssuccessors, using the function ’del’ and free(3).Finally, set the pointer to the list to NULL.13LibftYour very first own libraryFunction nameft<em>lstiterPrototypevoid ft</em>lstiter(t<em>list *lst, void (*f)(void *));Turn in files-Parameterslst:The address of a pointer to a node.f:The address of the function to apply to eachnode’s content.Return valueNoneExternal functs.NoneDescriptionIterates through the list ’lst’ and applies thefunction ’f’ to the content of each node.Function nameft</em>lstmapPrototypet<em>list *ft</em>lstmap(t_list <em>lst, void *(</em>f)(void <em>),void (</em>del)(void *));Turn in files-Parameterslst:The address of a pointer to a node.f:The address of the function applied to eachnode’s content.del:The address of the function used to delete anode’s content if needed.Return valueThe new list.NULL if the allocation fails.External functs.malloc, freeDescriptionIterates through the list ’lst’, applies thefunction ’f’ to each node’s content, and createsa new list resulting of the successive applicationsof the function ’f’.The ’del’ function is used todelete the content of a node if needed.14Chapter VSubmission and peer-evaluationSubmit your assignment in your Git repository as usual.Only the work inside yourrepository will be evaluated during the defense. Make sure to double-check the names ofyour files to ensure they are correct.Place all your files at the root of your repository.Rnpu cebwrpg va gur 42 Pbzzba Pber pbagnvaf na rapbqrq uvag. Sbe rnpupvepyr, bayl bar cebwrpg cebivqrf gur pbeerpg uvag arrqrq sbe gurarkg pvepyr. Guvf punyyratr vf vaqvivqhny, jvgu n svany cevmr sbebar fghqrag. Fgnss zrzoref znl cnegvpvcngr ohg ner abg ryvtvoyr sbe ncevmr. Ner lbh nzbat gur irel svefg gb fbyir n pvepyr? Fraq gur uvagfjvgu rkcynangvbaf gb by@42.se gb or nqqrq gb gur yrnqreobneq. Guruvag sbe guvf svefg cebwrpg, juvpu znl pbagnva nantenzzrq jbeqf, vf:Jbys bs ntragvir cnegvpyrf gung qvfcebir terral gb lbhe ubzrf qangung cebjfr lbhe fgbby15</p>