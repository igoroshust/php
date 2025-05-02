### Вставка HTML в PHP
- heredoc - это синтаксис в PHP, позволяющий создавать многострочные строки. Он удобен для работы с текстом, который может содержать как обычный текст, так и переменные, а также специальные символы, 
такие как кавычки, без необходимости экранирования. <br>

Благодаря `heredoc` можно вставлять HTML-разметку в PHP-код без потери стилей.

    <?php 
          foreach ($project_list as $items) {
                echo <<<HTML
                <li class='project'>
                   <a href='./project-page.html'>
                        <img src='{$items['img']}' alt='Project 1' class='project__img'>
                        <h3 class='project__title'>{$items['title']}</h3>
                   </a>
                </li>
                HTML;
          }
    ?>

- printf() или sprintf()

      foreach ($project_list as $items) {
        printf(
            "<li class='project'>
             <a href='./project-page.html'>
                <img src='%s' alt='Project 1' class='project__img'>
                <h3 class='project__title'>%s</h3>
             </a>
            </li>",
            htmlspecialchars($items['img'], ENT_QUOTES),
            htmlspecialchars($items['title'], ENT_QUOTES)
        );
      }
