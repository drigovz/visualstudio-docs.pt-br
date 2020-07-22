---
title: Atualizar o Visual Studio usando um layout mínimo de offline
description: Saiba como atualizar o Visual Studio usando um layout mínimo de offline.
ms.date: 07/21/2020
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 849cad46463ffb52e2f4f2a930f05daf66f7d737
ms.sourcegitcommit: 363f3e6e30dd54366ade0d08920755da5951535c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86869872"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>Atualizar o Visual Studio usando um layout mínimo de offline

Para computadores que não estão conectados à Internet, a criação de um layout mínimo é a maneira mais fácil e rápida de atualizar suas instâncias offline do Visual Studio.

A ferramenta de layout mínimo gera um layout adaptado especificamente às necessidades da sua equipe. Os administradores corporativos podem usar essa ferramenta para criar layout (s) de atualização para a maioria das versões do Visual Studio 2017 e 2019. Ao contrário de um layout completo do Visual Studio, um layout mínimo contém apenas os pacotes atualizados, portanto, é sempre menor e mais rápido para gerar e implantar. Você pode minimizar ainda mais o tamanho do layout de atualização especificando apenas os idiomas, as cargas de trabalho e os componentes desejados.

## <a name="how-to-generate-a-minimal-layout"></a>Como gerar um layout mínimo

> [!IMPORTANT]
> Essas instruções pressupõem que você já criou e usou layouts. Para obter mais informações sobre como fazer isso, consulte a página [atualizar uma instalação baseada em rede do Visual Studio](update-a-network-installation-of-visual-studio.md) .
>
> Para obter uma melhor compreensão do ciclo de vida do Visual Studio, consulte a página [ciclo de vida do produto e manutenção do Visual Studio](/visualstudio/releases/2019/servicing) .
>

Essa ferramenta cria layouts de atualização para o Visual Studio 2017 (15,9) e em diante. O layout pode ser implantado em computadores de rede/offline para atualizar instâncias do Visual Studio. Durante a [criação do layout normal](update-a-network-installation-of-visual-studio.md), todos os pacotes para essa versão específica são baixados. A criação de layout normal é necessária para reparar, desinstalar e outras operações padrão em instâncias do Visual Studio. O layout mínimo baixa apenas pacotes atualizados, portanto, é menor e mais fácil copiar para computadores offline.

### <a name="installing-the-minimal-layout-tool"></a>Instalando a ferramenta de layout mínimo
 
 1. Primeiro, baixe a ferramenta de layout mínimo localizada [aqui](https://aka.ms/vs/installer/minimallayout). Certifique-se de escolher **salvar** quando solicitado e, em seguida, selecione **executar**.

     ![Salvar ferramenta de layout mínimo](media/save-minimal-layout.png)

 2. Em seguida, aceite o prompt de controle de conta de usuário clicando em **Sim**.

     ![Aceitar controle de conta de usuário](media/accept-user-account-control.png)

 3. A ferramenta de layout mínimo será instalada no `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout` .

### <a name="how-to-use-the-minimal-layout-tool"></a>Como usar a ferramenta de layout mínimo

`MinimalLayout.exe`usa os comandos e opções a seguir para gerar o layout. Pelo menos um comando é necessário para executar a ferramenta. Veja como você executará a ferramenta:

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>Comandos
* **Visualização**: Use este comando para visualizar quantos pacotes serão baixados e o espaço total usado para criar esse layout. 
* **Gerar**: Use este comando para gerar o layout mínimo para atualizar o Visual Studio.
* **Regenerar**: Use este comando para regenerar um layout usando um arquivo de resposta de layout mínimo existente. Cada layout mínimo produz um `MinimalLayout.json` arquivo de resposta, que contém os parâmetros de entrada de layout mínimos originais. Você pode usar o comando **regenerar** e um `MinimalLayout.json` arquivo de resposta para regenerar o layout mínimo. Isso será útil se você quiser criar um layout mínimo para uma nova atualização do Visual Studio com base no arquivo de resposta do layout mínimo anterior. 
   - Para esse comando, `MinimalLayout.json` é necessário um caminho de arquivo de um layout já gerado. 

        ```cmd
        MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
        ```

* **Verificar**: Use este comando para determinar se a pasta de layout está corrompida.
* **Correção**: Use esse comando para corrigir uma pasta de layout corrompida, incluindo a substituição de pacotes ausentes da pasta de layout.

#### <a name="options"></a>Opções 

|Opções    |Descrição    |Obrigatório/Opcional |Exemplo |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt; dir&gt; |Especifica um diretório no qual criar um layout mínimo de offline.       |Obrigatório        |--targetLocation c:\VSLayout\ |
|--versão do baseVersion &lt;&gt;|O layout mínimo de offline será gerado começando com esta versão.   |Obrigatório|--baseVersion 16.4.0 |
|--versão do targetVersion &lt;&gt;|O layout mínimo de offline será gerado até e incluindo esta versão.|Obrigatório|--targetVersion 16.4.4|
|--idiomas    |Especifica os idiomas a serem incluídos no layout mínimo de offline. Vários valores podem ser especificados, separados por espaços.    |Obrigatório    |--idiomas en-US fr-FR |
|--ID de productId &lt;&gt;    |A ID do produto do qual o layout mínimo do offline será gerado. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul>|Obrigatório|--productId Microsoft. VisualStudio. Product. Enterprise |
|--filePath    |O caminho do arquivo do MinimalLayout.jsno arquivo de um layout já criado. Essa opção só é usada com o comando Regenerate.     |Necessário para regenerar o comando    |--filePath C:\VSLayout\minimalLayout.jsem <br><br> **Observe que o comando regenerar apenas usa--filePath como uma opção.** |
|--Adicionar &lt; uma ou mais IDs de carga de trabalho ou componente&gt;    |Especifica uma ou mais cargas de trabalho ou IDs de componente a serem adicionadas. Componentes adicionais podem ser adicionados globalmente usando--includeRecommended e/ou <br> –-includeOptional. Várias cargas de trabalho ou IDs de componentes podem ser especificados, separados por um espaço.    |Opcional    |--adicionar Microsoft. VisualStudio. Workload. ManagedDesktop Microsoft. VisualStudio. Workload. NetWeb Component. GitHub. VisualStudio |
|--includeRecommended    |Inclui os componentes recomendados para as cargas de trabalho que estão instaladas, mas não os componentes opcionais.    |Opcional    |Para uma carga de trabalho específica: <br> --adicionar Microsoft. VisualStudio. Workload. ManagedDesktop;includeRecommended <br><br> Para aplicar a todas as cargas de trabalho:--includeRecommended |
|--includeOptional |Inclui os componentes opcionais para todas as cargas de trabalho instaladas, incluindo os componentes recomendados.    |Opcional    |Para uma carga de trabalho específica: <br>--adicionar Microsoft. VisualStudio. Workload. ManagedDesktop;includeOptional <br><br> Para aplicar a todas as cargas de trabalho:--includeOptional |

### <a name="generating-a-minimal-layout"></a>Gerando um layout mínimo

> [!IMPORTANT]
>  Essas instruções pressupõem que você criou anteriormente um layout de instalação de rede. Para obter mais informações sobre como fazer isso, consulte a página [criar uma instalação de rede do Visual Studio](create-a-network-installation-of-visual-studio.md) .

Crie um layout mínimo usando o comando **Generate** para o intervalo especificado de versões. Você também precisará conhecer o productId, os idiomas e as cargas de trabalho específicas necessárias. Esse layout mínimo atualizará qualquer instância do Visual Studio da versão base até e incluindo a versão de destino.

Antes de criar o layout, você pode descobrir o tamanho total do download e o número de pacotes incluídos usando o comando **Preview** . Esse comando usa as mesmas opções que o comando **Generate** e os detalhes são gravados no console.

Vamos examinar alguns exemplos de como Visualizar, gerar e regenerar um layout mínimo:

- Primeiro, aqui está um exemplo de como Visualizar um layout para Visual Studio Enterprise versões 16.4.0 para 16.4.4 apenas em inglês.

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
    ```

- Veja como gerar esse mesmo layout com uma carga de trabalho.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- E aqui está como regenerar um layout mínimo de offline usando um arquivo de resposta existente. 

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

Alguns outros exemplos que usam o comando **Generate** :

- Veja como adicionar uma carga de trabalho adicional e incluir apenas os pacotes recomendados. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- E, finalmente, aqui está como você incluiria vários idiomas em seu layout mínimo. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

### <a name="how-to-maintain-a-minimal-layout"></a>Como manter um layout mínimo

Use os comandos **Verify** e **Fix** para manter o layout mínimo após sua criação. O comando **Verify** determina se há pacotes corrompidos ou ausentes no layout mínimo. Se você encontrar algum problema depois de executar o comando **Verify** , use o comando **corrigir** para corrigir os pacotes ausentes ou corrompidos.

- Veja como verificar se um layout tem pacotes corrompidos ou ausentes: 

    ```cmd
    MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
    ```

- E aqui está como corrigir esse layout:

    ```cmd
    MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
    ```

>[!NOTE] 
> Esse layout não pode ser usado para reparar uma instalação do Visual Studio. Para reparar uma instância existente do Visual Studio, consulte [reparar o Visual Studio](repair-visual-studio.md).
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>Como usar um layout mínimo offline para atualizar uma instalação existente do Visual Studio

Depois de gerar um layout mínimo, você pode copiar toda a pasta de layout mínima para um computador cliente. Isso será necessário se o computador não tiver acesso à pasta de layout mínima em seu local original.

Navegue até a pasta e identifique o nome do aplicativo bootstrapper. O nome do aplicativo bootstrapper depende do valor de ProductId especificado ao gerar o layout mínimo. Consulte a tabela abaixo para obter exemplos comuns.

|Valor de ProductId    |Nome do aplicativo|
|:-----------|:------------|
|Microsoft.VisualStudio.Product.Enterprise    |vs_enterprise.exe|
|Microsoft.VisualStudio.Product.Professional    |vs_professional.exe|
|Microsoft.VisualStudio.Product.BuildTools    |vs_buildtools.exe|

A atualização é aplicada a uma instância do Visual Studio em duas etapas. Comece atualizando o Instalador do Visual Studio e, em seguida, atualize o Visual Studio.

1. **Atualizar o Instalador do Visual Studio** 

    Execute o comando a seguir, substituindo `vs_enterprise.exe` pelo nome do aplicativo bootstrapper correto, se necessário. 

    ```cmd
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Atualizar o aplicativo do Visual Studio**

    Para atualizar o Visual Studio, você precisa especificar o installPath da instância do Visual Studio que deseja atualizar. Se várias instâncias do Visual Studio estiverem instaladas, cada uma precisará ser atualizada separadamente. É altamente recomendável que você especifique a `–noWeb` opção com o comando de atualização para impedir a instalação de componentes que não estão no layout mínimo. Isso impede que você deixe o Visual Studio em um estado inutilizável.

    Execute o comando a seguir, substituindo adequadamente o parâmetro de linha de comando installPath. Certifique-se de usar também o nome do aplicativo bootstrapper correto.

    ```cmd
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Veja também

* [Instalar o Visual Studio](install-visual-studio.md)
* [Guia do administrador do Visual Studio](visual-studio-administrator-guide.md)
* [Usar parâmetros de linha de comando para instalar o Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Ferramentas para detectar e gerenciar instâncias do Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Como definir as configurações em um arquivo de resposta](automated-installation-with-response-file.md)
* [Atualizações de controle para implantações do Visual Studio com base em rede](controlling-updates-to-visual-studio-deployments.md)
* [Ciclo de vida do produto Visual Studio e manutenção](/visualstudio/releases/2019/servicing/)
