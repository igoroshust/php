### Вывести список постов 

Моё решение:

    <?php
  
    $project_list = [
        ["img" => "./img/projects/01.jpg", "title" => "Gaming streaming portal"],
        ["img" => "./img/projects/02.jpg", "title" => "Video Service"],
        ["img" => "./img/projects/03.jpg", "title" => "Video Portal"],
        ["img" => "./img/projects/5.jpg", "title" => "Dating app"],
        ["img" => "./img/projects/6.jpg", "title" => "Landing"],
        ["img" => "./img/projects/7.jpg", "title" => "Gaming community"]
    ];

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

Решение учителя 

    // файл main.tpl

        <main class="section">
        <div class="container">
            <h2 class="title-1">Projects</h2>
            <ul class="projects">

            <?php

                foreach ($projects as $project) {
                    // var_dump($project);
                    include(ROOT . 'templates/project_card.tpl'); // для каждого проекта подключаем шаблон
                }

            </ul>
        </div>
    </main>

    // файл project_card.tpl

    <li class='project'>
        <a href='./project-page.html'>
            <img src='./img/projects/<?= $project['title'] ?>' alt='<?= $project['title'] ?>' class='project__img'>
            <h3 class='project__title'><?= $project['title'] ?></h3>
        </a>
    </li>


### Написать программу с выводом текущей даты

    function getCurrentYear()
    {
        return ((int) substr(date('Y-m-d'), 0, 4));
    }

    $result = getCurrentYear();
    echo $result;
