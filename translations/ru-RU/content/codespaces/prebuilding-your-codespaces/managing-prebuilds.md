---
title: Управление предварительными сборками
shortTitle: Manage prebuilds
intro: 'Вы можете просматривать, изменять и удалять конфигурации предварительной сборки для репозитория.'
versions:
  fpt: '*'
  ghec: '*'
type: how_to
topics:
  - Codespaces
miniTocMaxHeadingLevel: 3
ms.openlocfilehash: f39c46d91193db4c1c44ab336d86024b40adcea4
ms.sourcegitcommit: e8c012864f13f9146e53fcb0699e2928c949ffa8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2022
ms.locfileid: '148160191'
---
## Проверка, изменение и удаление конфигураций предварительной сборки

Предварительные сборки, настроенные для репозитория, создаются и обновляются с помощью рабочего процесса {% data variables.product.prodname_actions %} под управлением службы {% data variables.product.prodname_github_codespaces %}. 

В зависимости от параметров в конфигурации предварительной сборки, рабочий процесс обновления для предварительной сборки может активироваться следующими событиями:

* создание или обновление конфигурации предварительной сборки;
* отправка фиксации или запроса на вытягивание в ветвь, для которой настроены предварительные сборки;
* изменение любого из файлов конфигурации для контейнера разработки;
* активация события по расписанию, которое определено в конфигурации предварительной сборки;
* активация этого рабочего процесса вручную.

Параметры в конфигурации предварительной сборки определяют, какие события активируют автоматическое обновление предварительной сборки. Дополнительные сведения см. в разделе [Настройка предварительных сборок](/codespaces/prebuilding-your-codespaces/configuring-prebuilds#configuring-prebuilds). 

Пользователи с правами администратора в репозитории могут проверять ход выполнения предварительных сборок, изменять и удалять конфигурации предварительной сборки. 

### Просмотр хода выполнения для предварительной сборки
Текущее состояние последнего запуска рабочего процесса для каждой настроенной конфигурации предварительной сборки можно просмотреть на странице {% data variables.product.prodname_github_codespaces %} параметров репозитория. Здесь может быть указаны значения вида "Выполняется" или "Последний запуск 1 час назад".

Чтобы просмотреть выходные данные журнала для последнего запуска рабочего процесса предварительной сборки, щелкните **Просмотреть выходные данные**.

![Кнопка "Просмотреть выходные данные"](/assets/images/help/codespaces/prebuilds-see-output.png) 

Это действие отображает на вкладке **Действия** выходные данные последнего запуска рабочего процесса.

![Выходные данные рабочего процесса предварительной сборки](/assets/images/help/codespaces/prebuilds-log-output.png) 

Кроме того, вы можете просмотреть все запуски рабочего процесса предварительной сборки, связанные с указанной ветвью, нажав кнопку с многоточием и выбрав в раскрывающемся меню пункт **Просмотреть запуски**.

![Параметр "Просмотр запусков" в раскрывающемся меню](/assets/images/help/codespaces/prebuilds-view-runs.png) 

Отобразится журнал выполнения рабочего процесса предварительной сборки для связанной ветви.

![Просмотр истории выполнения рабочего процесса](/assets/images/help/codespaces/prebuilds-workflow-runs.png) 

### Изменение конфигурации предварительной сборки

1. На странице параметров репозитория для {% data variables.product.prodname_codespaces %} щелкните многоточие справа от конфигурации предварительной сборки, которую вы хотите изменить.
1. В раскрывающемся меню выберите **Изменить**.
 
   ![Параметр "Изменить" в раскрывающемся меню](/assets/images/help/codespaces/prebuilds-edit.png) 

1. Внесите необходимые изменения в конфигурацию предварительной сборки и щелкните **Обновить**. 

   {% data reusables.codespaces.prebuilds-permission-authorization %}


### Отключение конфигурации предварительной сборки

Чтобы приостановить обновление предварительных сборок для конфигурации, можно отключить для нее выполнения рабочего процесса. Отключение выполнений рабочего процесса для конфигурации предварительной сборки не удаляет ранее созданные предварительные сборки для этой конфигурации, а значит экземпляры codespace будут по-прежнему успешно создаваться из существующей предварительной сборки.

Отключение выполнения рабочих процессов для конфигурации предварительной сборки полезно, если необходимо исследовать сбои при создании предварительной сборки.

1. На странице параметров репозитория для {% data variables.product.prodname_codespaces %} щелкните многоточие справа от конфигурации предварительной сборки, которую вы хотите отключить.
1. В раскрывающемся меню выберите **Отключить запуски**.

   ![Параметр "Отключить запуски" в раскрывающемся меню](/assets/images/help/codespaces/prebuilds-disable.png)

1. Чтобы подтвердить намерение отключить эту конфигурацию, щелкните **ОК**.

### Удаление конфигурации предварительной сборки

При удалении конфигурации предварительной сборки также удаляются все ранее созданные для нее предварительные сборки. Это означает, что вскоре после удаления конфигурации все созданные ею предварительные сборки станут недоступными для создания нового пространства кода.

После удаления конфигурации предварительной сборки продолжится выполнение всех рабочих процессов, которые уже была поставлены в очередь или запущены для этой конфигурации. Они будут указаны в журнале выполнения рабочего процесса наряду со всеми ранее завершенными запусками рабочего процесса.

1. На странице параметров репозитория для {% data variables.product.prodname_codespaces %} щелкните многоточие справа от конфигурации предварительной сборки, которую вы хотите удалить.
1. В раскрывающемся меню выберите **Удалить**.

   ![Параметр "Удалить" в раскрывающемся меню](/assets/images/help/codespaces/prebuilds-delete.png)

1. Чтобы подтвердить удаление, щелкните **ОК**.

### Запуск предварительных сборок вручную

Иногда бывает нужно вручную запустить рабочий процесс для конфигурации предварительной сборки. Обычно это используется только при отладке проблем с рабочим процессом для конфигурации предварительной сборки.

1. На странице параметров репозитория для {% data variables.product.prodname_codespaces %} щелкните многоточие справа от конфигурации предварительной сборки, для которой вы хотите запустить рабочий процесс.
1. В раскрывающемся меню щелкните **Активировать вручную**.

   ![Параметр "Триггер вручную" в раскрывающемся меню](/assets/images/help/codespaces/prebuilds-manually-trigger.png) 

## Дополнительные материалы

- [Устранение неполадок с предварительными сборками](/codespaces/troubleshooting/troubleshooting-prebuilds)