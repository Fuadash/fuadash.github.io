---
layout: page
title: Memo Maker
description: Core Java CLI application that lets me quickly make memos in text file format. Still updated here and there whenever I have a feature to add.
img: 
importance: 1
category: fun
---

Technologies: Java, LLM integration, Docker (soon)

Hosted over at: <a href="https://github.com/Fuadash/memo-maker">https://github.com/Fuadash/memo-maker</a>

A couple of snippets below just to show a crumb of what is happening in the project.

{% raw %}

```java
public static void parseInput(String input) {
        if (input.toLowerCase().startsWith("!find")){
            String searchTarget = input.substring(5);
            Path root = Path.of(MemoConfig.getBasePath() + "logs");
            List<Path> pathToMemos = MemoSearcher.searchMemosFor(root, searchTarget);
            pathToMemos.forEach(System.out::println); //TODO: Make this only print like 10 at a time, maybe move into a memoprinter class
        }
        else if (input.toLowerCase().startsWith("!gpt")){
            System.out.println(GPTSummary.getSummary());
        }
        else {
            MemoLogger.logMemo(input, new MultiDate());
        }
    }
```

{% endraw %}

Standard parsing for inputs from the entry point, nothing big here.

{% raw %}

```java
public class MemoConfig {
    private static final Properties properties = new Properties();

    static {
        Optional<String> env = Optional.ofNullable(System.getenv("APP_ENV"));
        env.ifPresentOrElse(appEnv -> {
            // Gets the appropriate config file
            try (InputStream resources = MemoConfig.class.getClassLoader().getResourceAsStream("resources/" + appEnv + "/config.properties")) {
                properties.load(resources);
            } catch (IOException e) {
                e.printStackTrace();
            }
        },
        () -> {
            // Defaults to production for now since that's just the .jar
            try (InputStream input = MemoConfig.class.getClassLoader().getResourceAsStream("resources/prod/config.properties")) {
                properties.load(input);
            } catch (IOException e) {
                e.printStackTrace();
            }
        });
    }

    public static String getBasePath() {
        return properties.getProperty("file.path");
    }
}
```

{% endraw %}

The coolest bit (to me anyway). Uses the ofNullable to let the program act depending on the environment it's run in.

The shell for the GPT integration has been written and exists in the repo but is not included here but will be soon (when I get around to setting up billing with OpenAI). 
Docker integration also coming soon since I hear that is a little more convenient that carrying a jar around, and I just learnt how to use Docker (as of February 2024) so might as well.