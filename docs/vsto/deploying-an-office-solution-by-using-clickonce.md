---
title: Implantar uma solução de Office usando o ClickOnce
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4adbd08d13d26c717beeb454bd323185bb88640
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416556"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>Implantar uma solução de Office usando o ClickOnce
  Você pode implantar sua solução office em menos etapas se você usar O ClickOnce. Se você publicar atualizações, sua solução vai detectá-las e instalá-las automaticamente. No entanto, o ClickOnce exige que sua solução seja instalada separadamente para cada usuário de um computador. Portanto, você deve considerar o uso do Windows Installer (*.msi*) se mais de um usuário executar sua solução no mesmo computador.

## <a name="in-this-topic"></a>Neste tópico

- [Publicar a solução](#Publish)

- [Decidir como deseja conceder confiança à solução](#Trust)

- [Ajudar usuários a instalar a solução](#Helping)

- [Colocar o documento de uma solução no computador do usuário final (somente personalizações no nível de documento)](#Put)

- [Colocar o documento de uma solução em um servidor que está executando o SharePoint (somente personalizações no nível de documento)](#SharePoint)

- [Criar um instalador personalizado](#Custom)

- [Publicar uma atualização](#Update)

- [Alterar o local de instalação de uma solução](#Location)

- [Reverter uma solução para uma versão anterior](#Roll)

  Para obter mais informações sobre como implantar uma solução do Office criando um arquivo do Windows Installer, consulte [Implantar uma solução do Office usando o Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="publish-the-solution"></a><a name="Publish"></a>Publique a solução
 Você pode publicar sua solução usando o **Assistente de Publicação** ou o Designer de **Projeto**. Neste procedimento, você usará o **Project Designer** porque ele fornece o conjunto completo de opções de publicação. Consulte [O desenvolvimento do assistente de &#40;Office em Visual Studio&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md).

#### <a name="to-publish-the-solution"></a>Para publicar a solução

1. No **Solution Explorer,** escolha o nó nomeado para o seu projeto.

2. Na barra de menus, escolha **Project**, *ProjectName* **Properties**.

3. No **Project Designer,** escolha a guia **Publicar,** que a ilustração a seguir mostra.

    ![A guia publicar do Project Designer](../vsto/media/vsto-publishtab.png "A guia publicar do Project Designer")

4. Na caixa **Local da pasta de publicação (servidor ftp ou caminho de arquivo),** digite o caminho da pasta onde deseja que o **Projetista** copie os arquivos da solução.

    Você pode inserir qualquer um destes tipos de caminho.

   - Um caminho local (por exemplo, *C:\FolderName\FolderName*).

   - Um caminho de Convenção de Nomeação Uniforme (UNC) para uma pasta na rede (por exemplo, * \\\ServerName\FolderName*).

   - Um caminho relativo (por exemplo, *PublishFolder\\*, que é a pasta na qual o projeto é publicado por padrão).

5. Na caixa **URL da pasta de instalação,** digite o caminho totalmente qualificado do local onde os usuários finais encontrarão sua solução.

    Se você ainda não sabe a localização, não insira nada neste campo. Por padrão, o ClickOnce procura atualizações na pasta da qual seus usuários instalam a solução.

6. Escolha o botão **Pré-requisitos**.

7. Na caixa de diálogo **Pré-requisitos,** certifique-se de que o programa Criar configuração para instalar a caixa de **seleção de componentes pré-requisitos** seja selecionado.

8. Na **Escolha quais pré-requisitos para instalar a** lista, selecione as caixas de seleção do **Windows Installer 4.5** e o pacote .NET Framework apropriado.

    Por exemplo, se a [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]solução tiver como alvo o , selecione as caixas de seleção para **o Windows Installer 4.5** e **o Microsoft .NET Framework 4.5 Full**.

9. Se sua solução tiver como alvo o .NET Framework 4.5, selecione também as **ferramentas do Visual Studio 2010 para a caixa de seleção Office Runtime.**

    > [!NOTE]
    > Por padrão, esta caixa de seleção não aparece. Para mostrá-la, é preciso criar um pacote Bootstrapper. Consulte [Criar um pacote Bootstrapper para um Office 2013 VSTO Add-in com o Visual Studio 2012](create-vsto-add-ins-for-office-by-using-visual-studio.md).

10. Em **Especificar o local de instalação para pré-requisitos,** escolha uma das opções que aparecem e escolha o botão **OK.**

     A tabela a seguir descreve cada opção.

    |Opção|Descrição|
    |------------|-----------------|
    |**Baixar os pré-requisitos no site do fornecedor do componente**|É solicitado que o usuário baixe e instale esses pré-requisitos do fornecedor.|
    |**Baixar os pré-requisitos no mesmo local do meu aplicativo**|O software de pré-requisito é instalado com a solução. Se você escolher essa opção, o Visual Studio copiará todos os pacotes do pré-requisito no local de publicação. Para que essa opção funcione, os pacotes do pré-requisito devem estar no computador de desenvolvimento.|
    |**Baixar os pré-requisitos no seguinte local**|O Visual Studio copia todos os pacotes do pré-requisito no local que você especifica e os instala com a solução.|

     Consulte [a caixa de diálogo Pré-requisitos](../ide/reference/prerequisites-dialog-box.md).

11. Escolha o botão **Atualizações,** especifique quantas vezes deseja que o complemento ou personalização vsto de cada usuário final verifique se há atualizações e, em seguida, escolha o botão **OK.**

    > [!NOTE]
    > Se você estiver implantando usando um CD ou uma unidade removível, escolha o botão **Opção Nunca verificar atualizações.**

     Para obter informações sobre como publicar uma atualização, consulte [Publicar uma atualização](#Update).

12. Escolha o botão **Opções,** revise as opções na caixa de diálogo **Opções** e escolha o botão **OK.**

13. Escolha o botão **Publicar agora.**

     O Visual Studio adiciona as pastas e os arquivos a seguir à pasta de publicação que você especificou anteriormente neste procedimento.

    - A pasta **Arquivos de aplicativos.**

    - O programa de instalação.

    - Um manifesto de implantação que aponta para o manifesto de implantação da versão mais recente.

      A pasta **Arquivos de aplicativos** contém uma subpasta para cada versão que você publica. Cada subpasta específica da versão contém os arquivos a seguir.

    - Um manifesto de aplicativo.

    - Um manifesto de implantação.

    - Assemblies de personalização.

      A ilustração a seguir mostra a estrutura da pasta de publicação para um Complemento do Outlook VSTO.

      ![Publicar estrutura de pastas](../vsto/media/publishfolderstructure.png "Publicar estrutura de pastas")

    > [!NOTE]
    > ClickOnce anexa a extensão *.deploy* a assembléias para que uma instalação segura do IIS (Internet Information Services, serviços de informação da Internet) não bloqueie os arquivos por causa de uma extensão insegura. Quando o usuário instala a solução, o ClickOnce remove a extensão *.deploy.*

14. Copie os arquivos da solução no local de instalação que você especificou anteriormente neste procedimento.

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a>Decida como você quer conceder confiança à solução
 Para que uma solução possa ser executada nos computadores dos usuários, você deve conceder confiança ou os usuários devem responder a uma solicitação de confiança quando instalam a solução. Para conceder confiança à solução, assine o manifesto usando um certificado que identifique um fornecedor conhecido e confiável. Consulte [Confiar na solução assinando os manifestos de aplicação e implantação](../vsto/granting-trust-to-office-solutions.md#Signing).

 Se você estiver implantando uma personalização em nível de documento e quiser colocar o documento em uma pasta no computador do usuário ou disponibilizar o documento em um site do SharePoint, certifique-se de que o Office confie na localização do documento. Consulte [Grant confia em documentos.](../vsto/granting-trust-to-documents.md)

## <a name="help-users-install-the-solution"></a><a name="Helping"></a>Ajude os usuários a instalar a solução
 Os usuários podem instalar a solução executando o programa de configuração, abrindo o manifesto de implantação ou durante a personalização em nível de documento, abrindo o documento diretamente. Como uma prática recomendada, os usuários devem instalar a solução usando o programa de instalação. As outras duas abordagens não garantem que o software pré-requisito seja instalado. Se os usuários desejarem abrir o documento do local de instalação, eles deverão adicioná-lo à lista de locais confiáveis na Central de Confiabilidade do aplicativo do Office.

### <a name="opening-the-document-of-a-document-level-customization"></a>Abrindo o documento de uma personalização no nível de documento
 Os usuários podem abrir o documento de uma personalização no nível de documento diretamente do local de instalação ou copiando o documento no computador local e, em seguida, abrindo a cópia.

 Como uma prática recomendada, os usuários devem abrir uma cópia do documento nos respectivos computadores para que vários usuários não tentem abrir a mesma cópia ao mesmo tempo. Para impor essa prática, você pode configurar o programa de instalação para copiar o documento nos computadores dos usuários. Consulte [Colocar o documento de uma solução no computador do usuário final (apenas personalizações em nível de documento)](#Put).

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>Instale a solução abrindo o manifesto de implantação a partir de um site do IIS
 Os usuários podem instalar uma solução do Office abrindo o manifesto de implantação na Web. No entanto, uma instalação segura do IIS (Internet Information Services, serviços de informação à Internet) bloqueará arquivos que tenham a extensão *.vsto.* O tipo de MIME deve ser definido no IIS para que você possa implantar uma solução do Office usando o IIS.

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>Para adicionar o tipo de MIME .vsto ao IIS 6.0

1. No servidor que está executando o IIS 6.0, escolha **Iniciar** > **todos os programas** > de**ferramentas** >  administrativas do**Gerenciador de Informações da Internet (IIS).**

2. Escolha o nome do computador, a pasta **Sites da Web** ou o site que você está configurando.

3. Na barra de menu, escolha**Propriedades de** **Ação** > .

4. Na guia **HTTP Headers,** escolha o botão **Tipos MIME.**

5. Na janela **Tipos MIME,** escolha o botão **Novo.**

6. Na janela **Tipo MIME,** digite **.vsto** como extensão, digite **o aplicativo/x-ms-vsto** como o tipo MIME e, em seguida, aplique as novas configurações.

    > [!NOTE]
    > Para que as alterações entrem em vigor, você deve reiniciar o Serviço de Publicação na World Wide Web ou aguardar até que o processo de trabalho seja reciclado. Em seguida, você deve lavar o cache de disco do navegador e, em seguida, tentar abrir o arquivo *.vsto* novamente.

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>Para adicionar o tipo .vsto MIME ao IIS 7.0

1. No servidor que está executando o IIS 7.0, escolha **Iniciar** > **todos os acessórios de programas** > **Accessories**.

2. Abra o menu de atalho para **Prompt de**comando e, em seguida, escolha Executar **como administrador.**

3. Na **caixa Abrir,** digite o seguinte caminho e escolha o botão **OK.**

    ```cmd
    %windir%\system32\inetsrv
    ```

4. Insira o comando a seguir e aplique as novas configurações.

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > Para que as alterações entrem em vigor, você deve reiniciar o Serviço de Publicação na World Wide Web ou deve aguardar até que o processo de trabalho seja reciclado. Em seguida, você deve lavar o cache de disco do navegador e, em seguida, tentar abrir o arquivo *.vsto* novamente.

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a>Coloque o documento de uma solução no computador do usuário final (apenas personalizações em nível de documento)
 Você pode copiar o documento da sua solução no computador do usuário final para eles criando uma ação pós-implantação. Dessa forma, o usuário não precisa copiar manualmente o documento do local de instalação para o computador depois de instalar sua solução. Você terá que criar uma classe que defina a ação pós-implantação, construa e publique a solução, modifique o manifesto do aplicativo e reiassine o manifesto de aplicação e implantação.

 Os procedimentos a seguir assumem que o nome do seu projeto é **ExcelWorkbook** e que você publica a solução em uma pasta criada chamada **C:\publicar** no seu computador.

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>Criar uma classe que defina a ação de pós-implantação

1. Na barra de menu, escolha > **'Adicionar** > **arquivo', novo projeto**. **File**

2. Na caixa de diálogo **Adicionar novo projeto,** no painel **Modelos instalados,** escolha a pasta **Windows.**

3. No **painel Modelos,** escolha o modelo **Biblioteca de** classe.

4. No **campo Nome,** **digite FileCopyPDA**e escolha o botão **OK.**

5. No **Solution Explorer,** escolha o projeto **FileCopyPDA.**

6. Na barra de menu, escolha **Projeto** > **Adicionar referência**.

7. Na guia **.NET,** adicione `Microsoft.VisualStudio.Tools.Applications.Runtime` referências e `Microsoft.VisualStudio.Tools.Applications.ServerDocument`.

8. Renomeie a classe para `FileCopyPDA` e substitua o conteúdo do arquivo pelo código. Esse código executa as seguintes tarefas:

   - Copia o documento na área de trabalho do usuário

   - Altera a propriedade _AssemblyLocation de um caminho relativo para um caminho totalmente qualificado para o manifesto de implantação.

   - Exclui o arquivo se o usuário desinstalar a solução.

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>Compilar e publicar a solução

1. No **Solution Explorer,** abra o menu de atalho para o projeto **FileCopyPDA** e, em seguida, escolha **'Construir ''Criar'.**

2. Abra o menu de atalho para o projeto **ExcelWorkbook** e, em seguida, escolha **Construir**.

3. Abra o menu de atalho para o projeto **ExcelWorkbook** e, em seguida, escolha **Adicionar referência**.

4. Na caixa de diálogo **Adicionar referência,** escolha a guia **'Projetos',** escolha **FileCopyPDA**e escolha o botão **OK.**

5. No **Solution Explorer,** escolha o projeto **ExcelWorkbook.**

6. Na barra de menu, escolha **Projeto** > **Nova Pasta**.

7. Digite **Dados**e escolha a tecla **Enter.**

8. No **Solution Explorer,** escolha a pasta **Dados.**

9. Na barra de menu, escolha **'Adicionar** > **item existente'.**

10. Na caixa de diálogo **Adicionar item existente,** navegue até o diretório de saída do projeto **ExcelWorkbook,** escolha o arquivo **ExcelWorkbook.xlsx** e escolha o botão **Adicionar.**

11. No **Solution Explorer** escolha o arquivo **ExcelWorkbook.xlsx.**

12. Na janela **Propriedades,** altere a propriedade **'''Criar ação'** para **Conteúdo** e a propriedade **Copiar para diretório de saída para** copiar se for mais **nova**.

     Quando você concluir essas etapas, seu projeto se assemelhará à seguinte ilustração.

     ![Estrutura do projeto da ação pós-implantação.](../vsto/media/vsto-postdeployment.png "Estrutura do projeto da ação pós-implantação.")

13. Publique o projeto **ExcelWorkbook.**

### <a name="modify-the-application-manifest"></a>Modificar o manifesto de aplicativo

1. Abra o diretório de solução, **c:\publish,** usando **File Explorer**.

2. Abra a pasta **Arquivos de aplicativo** e abra a pasta que corresponde à versão publicada mais recente da sua solução.

3. Abra o arquivo **ExcelWorkbook.dll.manifest** em um editor de texto como O Bloco de Notas.

4. Depois do elemento `</vstav3:update>`, adicione o código a seguir. Para o atributo `<vstav3:entryPoint>` de classe do elemento, use a seguinte sintaxe: *NamespaceName.ClassName*. No exemplo a seguir, os nomes de classe e o namespace são iguais, de modo que o nome do ponto de entrada resultante é `FileCopyPDA.FileCopyPDA`.

    ```xml
    <vstav3:postActions>
      <vstav3:postAction>
        <vstav3:entryPoint
          class="FileCopyPDA.FileCopyPDA">
          <assemblyIdentity
            name="FileCopyPDA"
            version="1.0.0.0"
            language="neutral"
            processorArchitecture="msil" />
        </vstav3:entryPoint>
        <vstav3:postActionData>
        </vstav3:postActionData>
      </vstav3:postAction>
    </vstav3:postActions>
    ```

### <a name="re-sign-the-application-and-deployment-manifests"></a>Assinar novamente os manifestos de aplicativo e implantação

1. Na pasta **%USERPROFILE":"USERPROFILE":"\Documents\Visual Studio 2013\Projects\ExcelWorkbook\ExcelWorkbook,** copie o arquivo de certificado **ExcelWorkbook_TemporaryKey.pfx** e cole-o na pasta *PublishFolder\Application* **Files\ExcelWorkbook**\__MaisrecentePublicadoVersão._

2. Abra o prompt de comando do Visual Studio e, em seguida, altere os diretórios para a pasta **c:\publish\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_ (por exemplo, **c:\publish\Application Files\ExcelWorkbook_1_0_0_4**).

3. Assine o manifesto de aplicativo modificado executando o seguinte comando:

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     A mensagem "ExcelWorkbook.dll.manifest assinado com êxito" é exibida.

4. Altere para a pasta **c:\publicar** e, em seguida, atualize e assine o manifesto de implantação executando o seguinte comando:

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > No exemplo anterior, substitua MostRecentVersionNumber pelo número da versão da versão mais recente publicada da sua solução (por exemplo, **1_0_0_4**).

     A mensagem "ExcelWorkbook.vsto assinado com êxito" é exibida.

5. Copie o arquivo *ExcelWorkbook.vsto* para o diretório **c:\publish\Application Files\ExcelWorkbook**\__MostRecentVersionNumber._

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a>Coloque o documento de uma solução em um servidor que está executando o SharePoint (apenas personalizações em nível de documento)
 Você pode publicar sua personalização no nível de documento para os usuários finais usando o SharePoint. Quando os usuários acessam o site do SharePoint e abrem o documento, o runtime instala a solução automaticamente da pasta de rede compartilhada no computador local do usuário. Depois que a solução estiver localmente instalada, a personalização continuará funcionando mesmo que o documento seja copiado em qualquer lugar, como na área de trabalho, por exemplo.

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>Para colocar o documento em um servidor que está executando o SharePoint

1. Adicione o documento da solução a uma biblioteca de documentos em um site do SharePoint.

2. Execute as etapas de uma das abordagens a seguir:

    - Use a Ferramenta de Configuração do Office para adicionar o servidor que está executando o SharePoint à Central de Confiabilidade no Word ou Excel em todos os computadores dos usuários.

         Consulte [políticas e configurações de segurança no Office 2010](/previous-versions/office/office-2010/cc178946(v=office.14)).

    - Assegure-se de que cada usuário execute as etapas a seguir.

        1. No computador local, abra o Word ou o Excel, escolha a guia **Arquivo** e escolha o botão **Opções.**

        2. Na caixa de diálogo **Do Centro** de Confiança, escolha o botão **Locais confiáveis.**

        3. Selecione a **caixa de seleção Permitir locais confiáveis na minha rede (não recomendada)** e, em seguida, escolha o botão **Adicionar novo local.**

        4. Na caixa **Caminho,** digite a URL da biblioteca de documentos do SharePoint *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*que contém o documento que você carregou (por exemplo, ).

             Não adicione o nome da página da Web padrão, como *default.aspx* ou *AllItems.aspx*.

        5. Selecione as **subpastas deste local também são caixa de** seleção confiável e, em seguida, escolha o botão **OK.**

             Quando os usuários abrem o documento no site do SharePoint, ele é aberto e a personalização é instalada. Os usuários podem copiar o documento na respectiva área de trabalho. A personalização ainda será executada porque as propriedades no documento apontam para o local de rede do documento.

## <a name="create-a-custom-installer"></a><a name="Custom"></a>Criar um instalador personalizado
 Você pode criar um instalador personalizado para sua solução office, em vez de usar o programa de configuração criado para você quando publicar a solução. Por exemplo, você pode usar um script de login para iniciar a instalação, ou pode usar um arquivo em lote para instalar a solução sem a interação do usuário. Esses cenários funcionarão melhor se os pré-requisitos já estiverem instalados nos computadores dos usuários finais.

 Como parte do seu processo de instalação personalizado, ligue para a ferramenta instalador para soluções do Office *(VSTOInstaller.exe),* que está instalada no seguinte local por padrão:

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 Se a ferramenta não estiver nesse local, você poderá usar a chave de registro **HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\VSTO Setup\v4\InstallerPath** ou **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Configuração de tempo de execução\v4\InstallerPath** para encontrar o caminho para essa ferramenta.

 Você pode usar os seguintes parâmetros com *VSTOinstaller.exe*.

| Parâmetro | Definição |
|------------------| - |
| /Install ou /I | Instale a solução. Você deve seguir essa opção com o caminho de um manifesto de implantação. Você pode especificar um caminho no computador local, um compartilhamento de arquivo da Convenção de Nomeação Universal (UNC). Você pode especificar um caminho local *(C:\FolderName\PublishFolder),* um caminho relativo *(Publicar)\\*ou um local totalmente qualificado*\\(\ServerName\FolderName* ou http://<em>ServerName/FolderName).</em> |
| /Uninstall ou /U | Desinstale a solução. Você deve seguir essa opção com o caminho de um manifesto de implantação. Você pode especificar que um caminho pode estar no computador local, um compartilhamento de arquivos UNC. Você pode especificar um caminho local *(c:\FolderName\PublishFolder),* um caminho relativo *(Publicar)\\*ou um local totalmente qualificado*\\(\ServerName\FolderName* ou http://<em>ServerName/FolderName</em>). |
| /Silent ou /S | Instale ou desinstale sem solicitar a interação do usuário ou sem exibição de mensagens. Se for necessário um prompt de confiança, a personalização não será instalada ou atualizada. |
| /Ajuda ou /? | Exiba as informações da Ajuda. |

 Quando você executa *VSTOinstaller.exe,* os seguintes códigos de erro podem aparecer.

|Código do Erro|Definição|
|----------------|----------------|
|0|A solução foi instalada ou desinstalada com êxito, ou a Ajuda do VSTOInstaller foi exibida.|
|-100|Uma ou mais opções de linha de comando não são válidas ou foram definidas mais de uma vez. Para obter mais informações, digite "vstoinstaller /?" ou consulte [Criar um instalador personalizado para uma solução ClickOnce Office](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e).|
|-101|Uma ou mais opções de linha de comando não são válidas. Para obter mais informações, insira "vstoinstaller /?".|
|-200|O uri manifesto de implantação não é válido. Para obter mais informações, insira "vstoinstaller /?".|
|-201|A solução não pôde ser instalada porque o manifesto de implantação não é válido. Consulte [manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md).|
|-202|A solução não pôde ser instalada porque a seção Visual Studio Tools for Office do manifesto de aplicativo não é válida. Consulte [manifestos de aplicativos para soluções do Office](../vsto/application-manifests-for-office-solutions.md).|
|-203|A solução não pôde ser instalada porque ocorreu um erro de download. Verifique o URI ou o local do arquivo de rede do manifesto de implantação e tente novamente.|
|-300|A solução não pôde ser instalada porque ocorreu uma exceção de segurança. Consulte [soluções do Secure Office](../vsto/securing-office-solutions.md).|
|-400|A solução não pôde ser instalada.|
|-401|A solução não poderia ser desinstalada.|
|-500|A operação foi cancelada porque a solução não pôde ser instalada ou desinstalada, ou o manifesto de implantação não pôde ser baixado.|

## <a name="publish-an-update"></a><a name="Update"></a>Publicar uma atualização
 Para atualizar uma solução, publique-a novamente usando o **Project Designer** ou O Assistente **de Publicação**e copie a solução atualizada para o local de instalação. Ao copiar os arquivos no local da instalação, verifique se substituiu os arquivos anteriores.

 Da próxima vez que a solução verificar uma atualização, ela encontrará e carregará a nova versão automaticamente.

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a>Alterar o local de instalação de uma solução
 É possível adicionar ou alterar o caminho de instalação depois que uma solução é publicada. Talvez seja conveniente alterar o caminho de instalação por um ou mais dos seguintes motivos:

- O programa de instalação foi compilado antes que o caminho de instalação fosse conhecido.

- Os arquivos da solução foram copiados em um local diferente.

- O servidor que hospeda os arquivos de instalação tem um novo nome ou local.

  Para alterar o caminho de instalação de uma solução, é preciso atualizar o programa de instalação e, em seguida, os usuários devem executá-lo. Para personalização no nível de documento, os usuários também devem atualizar uma propriedade no respectivo documento para que ele aponte para o novo local.

> [!NOTE]
> Se você não quiser pedir aos usuários para atualizar suas propriedades do documento, você pode pedir aos usuários para obter o documento atualizado a partir do local de instalação.

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>Para alterar o caminho de instalação no programa de instalação

1. Abra uma janela **Prompt de comando** e, em seguida, altere diretórios para a pasta de instalação.

2. Execute o programa de instalação e inclua o parâmetro `/url`, que usa o novo caminho de instalação como uma cadeia de caracteres.

    O exemplo a seguir mostra como alterar o caminho de instalação para um local no site da Fabrikam, mas você pode substituir essa URL pelo caminho que desejar:

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > Se uma mensagem for exibida informando que a assinatura do executável será invalidada, o certificado que foi usado para assinar a solução não é mais válida e o editor é desconhecido. Consequentemente, os usuários precisarão confirmar que confiam na origem da solução para que possam instalá-la.

   > [!NOTE]
   > Para exibir o valor atual da URL, execute `setup.exe /url`.

   Para personalizações em nível de documento, os usuários devem abrir o documento e, em seguida, atualizar sua propriedade _AssemblyLocation. As etapas a seguir descrevem como os usuários podem executar essa tarefa.

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>Para atualizar a propriedade _AssemblyLocation em um documento

1. Na guia **Arquivo,** escolha **'Informações',** que a ilustração a seguir mostra.

     ![Guia de informações no Excel](../vsto/media/vsto-infotab.png "Guia de informações no Excel")

2. Na lista **Propriedades,** escolha **Propriedades Avançadas**, que a ilustração a seguir mostra.

     ![Propriedades Avançadas no Excel.](../vsto/media/vsto-advanceddocumentproperties.png "Propriedades Avançadas no Excel.")

3. Na guia **Personalizado** na lista **Propriedades,** escolha _AssemblyLocation, como mostra a ilustração a seguir.

     ![A propriedade AssemblyLocation.](../vsto/media/vsto-assemblylocationproperty.png "A propriedade AssemblyLocation.")

     A **caixa Valor** contém o identificador manifesto de implantação.

4. Antes do identificador, digite o caminho totalmente qualificado do documento, seguido por uma barra, no formato*Identificador* *de Caminho*|(por exemplo, *File://ServerName/FolderName/FileName|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*.

     Para obter mais informações sobre como formatar esse identificador, consulte [Visão geral das propriedades dos documentos personalizados](../vsto/custom-document-properties-overview.md).

5. Escolha o botão **OK** e, em seguida, salve e feche o documento.

6. Execute o programa de instalação sem o parâmetro /url para instalar a solução no local especificado.

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a>Reverter uma solução para uma versão anterior
 Ao reverter uma solução, você reverte os usuários para uma versão anterior dessa solução.

#### <a name="to-roll-back-a-solution"></a>Para reverter uma solução

1. Abra o local de instalação da solução.

2. Na pasta de publicação de nível superior, exclua o manifesto de implantação (o arquivo *.vsto).*

3. Localize a subpasta da versão para a qual deseja fazer a reversão.

4. Copie o manifesto de implantação dessa subpasta na pasta de publicação superior.

     Por exemplo, para reverter uma solução chamada **OutlookAddIn1** da versão 1.0.0.1 para a versão 1.0.0.0, copie o arquivo **OutlookAddIn1.vsto** da pasta **OutlookAddIn1_1_0_0_0.** Cole o arquivo na pasta de publicação de nível superior, substituindo o manifesto de implantação específico da versão para **OutlookAddIn1_1_0_0_1** que já estava lá.

     A ilustração a seguir mostra a estrutura da pasta de publicação nesse exemplo.

     ![Publicar estrutura de pastas](../vsto/media/publishfolderstructure.png "Publicar estrutura de pastas")

     Da próxima vez que um usuário abrir o aplicativo ou o documento personalizado, a alteração do manifesto de implantação será detectada. A versão anterior da solução do Office é executada do cache do ClickOnce.

> [!NOTE]
> Os dados locais são salvos para apenas uma versão anterior de uma solução. Se você reverter duas versões, os dados locais não serão retidos. Para obter mais informações sobre dados locais, consulte [Acessar dados locais e remotos em aplicativos ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).

## <a name="see-also"></a>Confira também

- [Implantar uma solução de Office](../vsto/deploying-an-office-solution.md)
- [Publicar soluções do Escritório](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Como: Publicar uma solução do Office usando o ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Como: Instalar uma solução clickonce office](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)
- [Como: Publicar uma solução de Office em nível de documento para um servidor SharePoint usando o ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)
- [Crie um instalador personalizado para uma solução de escritório ClickOnce](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)