---
title: Usar parâmetros de linha de comando para instalar o Visual Studio
titleSuffix: ''
description: Saiba como usar parâmetros de linha de comando para controlar ou personalizar sua instalação do Visual Studio.
ms.date: 02/12/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e8d0fd308d7a5dcdea926cbd710f1a7a362738f1
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58325312"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Usar parâmetros de linha de comando para instalar o Visual Studio

Ao instalar o Visual Studio por meio de um prompt de comando, é possível usar uma variedade de parâmetros de linha de comando para controlar ou personalizar a instalação. Da linha de comando, você pode realizar as seguintes ações:

- Iniciar a instalação com certas opções pré-selecionadas.
- Automatizar o processo de instalação.
- Criar um cache (layout) dos arquivos de instalação para uso posterior.

As opções de linha de comando são usadas em conjunto com o bootstrapper de instalação, que é o arquivo pequeno (aproximadamente 1MB) que inicia o processo de download. O bootstrapper é o primeiro executável iniciado quando você baixa do site do Visual Studio. Use os links a seguir para obter um link direto para o bootstrapper de versão mais recente para a edição do produto que você está instalando:

- [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Comunidade do Visual Studio 2017](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)

## <a name="command-line-parameters"></a>Parâmetros de linha de comando

 Os parâmetros da linha de comando do Visual Studio diferenciam maiúsculas de minúsculas.

> Syntax: `vs_enterprise.exe [command] <options>...`

(Substitua `vs_enterprise.exe` conforme apropriado de acordo com a edição do produto que você está instalando.)

>[!TIP]
> Confira mais exemplos de como usar a linha de comando para instalar o Visual Studio na página [Exemplos de parâmetros de linha de comando](command-line-parameter-examples.md).

| **Comando** | **Descrição** |
| ----------------------- | --------------- |
| (blank) | Instala o produto. |
| `modify` | Modifica um produto instalado. |
| `update` | Atualiza um produto instalado. |
| `repair` | Repara um produto instalado. |
| `uninstall` | Desinstala um produto instalado. |
| `export` | **Novidades na versão 15.9**: Exporta a seleção da instalação para um arquivo de configuração de instalação. **Observação**: Só pode ser usado com vs_installer.exe. |

## <a name="install-options"></a>Opções de instalação

| **Opção de instalação** | **Descrição** |
| ----------------------- | --------------- |
| `--installPath <dir>` | O diretório de instalação no qual a instância deverá agir. Para o comando de instalação, isso é **Opcional** e é onde a instância será instalada. Para outros comandos, isso é **Necessário** e é onde a instância instalada anteriormente foi instalada. |
| `--addProductLang <language-locale>` | **Opcional**: Durante a instalação ou a operação de modificação, isso determina os pacotes de idiomas de interface do usuário que são instalados no produto. Ele pode aparecer várias vezes na linha de comando para adicionar vários pacotes de idiomas. Se não estiver presente, a instalação usará a localidade do computador. Para obter mais informações, consulte a seção [Lista de localidades de idioma](#list-of-language-locales) nesta página.|
| `--removeProductLang <language-locale>` | **Opcional**: Durante a instalação ou a operação de modificação, isso determina os pacotes de idiomas de interface do usuário que devem ser removidos do produto. Ele pode aparecer várias vezes na linha de comando para adicionar vários pacotes de idiomas. Para obter mais informações, consulte a seção [Lista de localidades de idioma](#list-of-language-locales) nesta página.|
| `--add <one or more workload or component IDs>` | **Opcional**: Uma ou mais IDs de carga de trabalho ou de componente a serem adicionadas. Os componentes obrigatórios do artefato são instalados, mas não os componentes recomendados ou opcionais. Você pode controlar os componentes adicionais globalmente usando `--includeRecommended` e/ou `--includeOptional`. Para incluir várias cargas de trabalho ou componentes, repita o comando `--add` (por exemplo, `--add Workload1 --add Workload2`). Para ter um controle mais refinado, você pode acrescentar `;includeRecommended` ou `;includeOptional` à ID (por exemplo, `--add Workload1;includeRecommended` ou `--add Workload2;includeRecommended;includeOptional`). Para saber mais, confira a página [IDs de carga de trabalho e de componente](workload-and-component-ids.md). Você pode repetir esta opção conforme necessário.|
| `--remove <one or more workload or component IDs>` | **Opcional**: Uma ou mais IDs de carga de trabalho ou de componente a serem removidas. Para obter mais informações, consulte nossa página [IDs de carga de trabalho e de componente](workload-and-component-ids.md). Você pode repetir esta opção conforme necessário.|
| `--in <path>` | **Opcional**: O URI ou o caminho para um arquivo de resposta.  |
| `--all` | **Opcional**: Indica se todas as cargas de trabalho e todos os componentes de um produto serão instalados. |
| `--allWorkloads` | **Opcional**: Instala todas as cargas de trabalho e todos os componentes, mas nenhum componente recomendado ou opcional. |
| `--includeRecommended` | **Opcional**: Inclui os componentes recomendados para as cargas de trabalho que estão instaladas, mas não os componentes opcionais. As cargas de trabalho são especificadas com `--allWorkloads` ou `--add`. |
| `--includeOptional` | **Opcional**: Inclui os componentes opcionais para as cargas de trabalho que estão instaladas, mas não os componentes recomendados. As cargas de trabalho são especificadas com `--allWorkloads` ou `--add`.  |
| `--quiet, -q` | **Opcional**: Não exibe nenhuma interface do usuário durante a instalação. |
| `--passive, -p` | **Opcional**: Exibe a interface do usuário, mas não solicita nenhuma interação do usuário. |
| `--norestart` | **Opcional**: Se essa opção estiver presente, os comandos com `--passive` ou `--quiet` não reiniciarão o computador automaticamente (se necessário).  Isso será ignorado se `--passive` e `--quiet` não forem especificados.  |
| `--nickname <name>` | **Opcional**: Define o apelido a ser atribuído a um produto instalado. O apelido não pode ter mais de 10 caracteres.  |
| `--productKey` | **Opcional**: Define a chave do produto (Product Key) a ser usada para um produto instalado. Ele é composto de 25 caracteres alfanuméricos no formato `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` ou `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Exibir uma versão offline desta página. |
| `--config <path>` | **Opcional** e **Novidades do 15.9**: Durante uma instalação ou uma operação de modificação, isso determina as cargas de trabalho e componentes a serem adicionados com base em um arquivo de configuração de instalação salvo anteriormente. Essa operação é aditiva e não removerá nenhuma carga de trabalho nem componente se ele não estiver presente no arquivo. Além disso, os itens que não se aplicarem ao produto não serão adicionados. Durante uma operação de exportação, isso determina a localização para salvar o arquivo de configuração de instalação. |

> [!IMPORTANT]
> Ao especificar várias cargas de trabalho e vários componentes, é necessário repetir a opção de linha de comando `--add` ou `--remove` para cada item.

## <a name="layout-options"></a>Opções de layout

| **Opções de layout** | **Descrição** |
| ----------------------- | --------------- |
| `--layout <dir>` | Especifica um diretório para criar um cache de instalação offline. Para obter mais informações, consulte [Criar uma instalação baseada em rede do Visual Studio](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Opcional**: Usado com `--layout` para preparar um cache de instalação offline com pacotes de recursos com os idiomas especificados. Para obter mais informações, consulte a seção [Lista de localidades de idioma](#list-of-language-locales) nesta página.|
| `--add <one or more workload or component IDs>` | **Opcional**: Uma ou mais IDs de carga de trabalho ou de componente a serem adicionadas. Os componentes obrigatórios do artefato são instalados, mas não os componentes recomendados ou opcionais. Você pode controlar os componentes adicionais globalmente usando `--includeRecommended` e/ou `--includeOptional`. Para ter um controle mais refinado, você pode acrescentar `;includeRecommended` ou `;includeOptional` à ID (por exemplo, `--add Workload1;includeRecommended` ou `--add Workload2;includeOptional`). Para saber mais, confira a página [IDs de carga de trabalho e de componente](workload-and-component-ids.md). <br/>**Observação**: Se `--add` for usado, somente as cargas de trabalho especificadas e os componentes e suas dependências serão baixados. Se `--add` não for especificado, todas as cargas de trabalho e componentes serão baixados para o layout.|
| `--includeRecommended` | **Opcional**: Inclui os componentes recomendados para as cargas de trabalho que estão instaladas, mas não os componentes opcionais. As cargas de trabalho são especificadas com `--allWorkloads` ou `--add`. |
| `--includeOptional` | **Opcional**: Inclui os componentes recomendados *e* opcionais para as cargas de trabalho incluídas no layout. As cargas de trabalho são especificadas com `--add`.  |
| `--keepLayoutVersion` | **Novidades do 15.3, opcionais**: Aplique alterações ao layout sem atualizar a versão do layout. |
| `--verify` | **Novidades do 15.3, opcionais**: Verifique o conteúdo de um layout. Todos os arquivos corrompidos ou ausentes são listados. |
| `--fix` | **Novidades do 15.3, opcionais**: Verifique o conteúdo de um layout.  Se algum arquivo estiver corrompido ou ausente, ele será baixado novamente. Para corrigir um layout, é necessário acesso à Internet. |
| `--clean <one or more paths to catalogs>` | **Novidades do 15.3, opcionais**: Remove versões antigas dos componentes de um layout que foi atualizado para uma versão mais recente. |

| **Opções de instalação avançadas** | **Descrição** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Opcional**: A ID do canal para a instância a ser instalada. Isso é necessário para o comando de instalação, ignorado para outros comandos se `--installPath` está especificado. |
| `--channelUri <uri>` | **Opcional**: O URI do manifesto do canal. Se as atualizações não forem desejadas, `--channelUri` poderá apontar para um arquivo inexistente. por exemplo, --channelUri C:\doesntExist.chman. Isso pode ser usado para o comando de instalação e é ignorado para outros comandos. |
| `--installChannelUri <uri>` | **Opcional**: O URI do manifesto do canal a ser usado para a instalação. O URI especificado por `--channelUri` (que deve ser especificado quando `--installChannelUri` for especificado) é usado para detectar atualizações. Isso pode ser usado para o comando de instalação e é ignorado para outros comandos. |
| `--installCatalogUri <uri>` | **Opcional**: O URI do manifesto do catálogo a ser usado para a instalação. Se especificado, o gerente de canal tenta baixar o manifesto do catálogo desse URI antes de usar o URI no manifesto do canal de instalação. Esse parâmetro é usado para dar suporte a instalação offline, em que o cache de layout será criado com o catálogo de produtos que já foi baixado. Isso pode ser usado para o comando de instalação e é ignorado para outros comandos. |
| `--productId <id>` | **Opcional** A ID do produto para a instância que será instalada. Isso será populado previamente em condições normais de instalação. |
| `--wait` | **Opcional**: O processo aguardará até que a instalação seja concluída antes de retornar um código de saída. Isso é útil ao automatizar instalações em que é necessário aguardar a conclusão da instalação para tratar o código de retorno da instalação. |
| `--locale <language-locale>` | **Opcional**: Altere o idioma de exibição da interface do usuário do próprio instalador. A configuração será mantida. Para obter mais informações, consulte a seção [Lista de localidades de idioma](#list-of-language-locales) nesta página.|
| `--cache` | **Novidades do 15.2, opcionais**: Caso estejam presentes, os pacotes serão mantidos após a instalação para reparos posteriores. Isso substitui a configuração de política global a ser usada para instalações, reparos ou modificações subsequentes. A política padrão é armazenar pacotes em cache. Isso é ignorado para o comando de desinstalação. Leia sobre como [desabilitar ou mover o cache do pacote](disable-or-move-the-package-cache.md) para obter mais informações. |
| `--nocache` | **Novidades do 15.2, opcionais**: Caso estejam presentes, os pacotes serão excluídos depois de serem instalados ou reparados. Serão baixados novamente apenas se for necessário e excluídos após o uso. Isso substitui a configuração de política global a ser usada para instalações, reparos ou modificações subsequentes. A política padrão é armazenar pacotes em cache. Isso é ignorado para o comando de desinstalação. Leia sobre como [desabilitar ou mover o cache do pacote](disable-or-move-the-package-cache.md) para obter mais informações. |
| `--noUpdateInstaller` | **Novidades do 15.2, opcionais**: Caso esteja presente, impede que o instalador atualize a si próprio quando o modo silencioso é especificado. O comando do instalador falhará e retornará um código de saída diferente de zero se noUpdateInstaller for especificado como silencioso quando uma atualização do instalador for necessária. |
| `--noWeb` | **Novidades do 15.3, opcionais**: Caso esteja presente, a instalação do Visual Studio usará os arquivos no diretório de layout para instalar o Visual Studio. Se o usuário tentar instalar componentes que não estejam no layout, a instalação falhará.  Para obter mais informações, consulte [Implantação de uma instalação de rede](create-a-network-installation-of-visual-studio.md). <br/><br/> **Importante**: Esta opção não impede a verificação de atualizações na instalação do Visual Studio. Para saber mais, confira a página [Controlar atualizações para implantações do Visual Studio baseadas em rede](controlling-updates-to-visual-studio-deployments.md).|
| `--path <name>=<path>` | **Novidades do 15.7, opcionais**: Usado para especificar caminhos de instalação personalizados para a instalação. Os nomes de caminho com suporte são shared, cache e install. |
| `--path cache=<path>` | **Novidades do 15.7, opcionais**: Usa a localização especificada para baixar os arquivos de instalação. Este local só pode ser definido na primeira vez em que o Visual Studio é instalado. Exemplo: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Novidades do 15.7, opcionais**: Contém arquivos compartilhados para instalações do Visual Studio lado a lado. Algumas ferramentas e SDKs fazem instalações em um local nessa unidade, enquanto outros podem substituir essa configuração e fazer a instalação em outra unidade. Exemplo: `--path shared="C:\VS\shared"` <br><br>Importante: Isso pode ser definido apenas uma vez e na primeira vez que o Visual Studio é instalado. |
| `--path install=<path>` | **Novidades do 15.7, opcionais**: Equivalente a `–-installPath`. Especificamente, `--installPath "C:\VS"` e `--path install="C:\VS"` são equivalentes. Apenas um deles pode ser usado por vez. |

## <a name="list-of-workload-ids-and-component-ids"></a>Lista de IDs de carga de trabalho e IDs de componente

Confira uma lista de IDs de componente e de carga de trabalho classificadas por produto do Visual Studio na página [IDs de componente e de carga de trabalho do Visual Studio](workload-and-component-ids.md).

## <a name="list-of-language-locales"></a>Lista de localidades de idioma

| **Localidade de idioma** | **Linguagem** |
| ----------------------- | --------------- |
| Cs-cz | Tcheco |
| De-de | Alemão |
| En-us | Inglês |
| Es-es | Espanhol |
| Fr-fr | Francês |
| It-it | Italiano |
| Ja-jp | Japonês |
| Ko-kr | Coreano |
| Pl-pl | Polonês |
| Pt-br | Português - Brasil |
| Ru-ru | Russo |
| Tr-tr | Turco |
| Zh-cn | Chinês – Simplificado |
| Zh-tw | Chinês – Tradicional |

## <a name="error-codes"></a>Códigos de erro

Dependendo do resultado da operação, a variável de ambiente `%ERRORLEVEL%` será definida como um dos valores a seguir:

| **Valor** | **Result** |
| --------- | ---------- |
| 0 | A operação foi concluída com êxito |
| 1602 | A operação foi cancelada |
| 3010 | A operação foi concluída com êxito, mas a instalação requer a reinicialização antes de ser usada |
| 5004 | A operação foi cancelada |
| 5007 | A operação foi bloqueada – o computador não atende aos requisitos |
| Outros | Condição de falha ocorreu. Verifique os logs para obter mais informações |

Cada operação gera vários arquivos de log no diretório `%TEMP%` que indicam o progresso da instalação. Classifique a pasta por data e procure arquivos começando com `dd_bootstrapper`, `dd_client` e `dd_setup` para o bootstrapper, o aplicativo instalador e o mecanismo de instalação, respectivamente.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulte também

- [Exemplos de parâmetros de linha de comando para a instalação do Visual Studio](command-line-parameter-examples.md)
- [Criar uma instalação offline do Visual Studio](create-an-offline-installation-of-visual-studio.md)
- [Automatizar a instalação do Visual Studio com um arquivo de resposta](automated-installation-with-response-file.md)
- [Carga de trabalho do Visual Studio e IDs do componente](workload-and-component-ids.md)