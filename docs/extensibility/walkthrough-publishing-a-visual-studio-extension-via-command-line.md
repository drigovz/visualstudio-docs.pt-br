---
title: Publicar extensão usando linha de comando
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40be0252218f39b4ff98b58caedd7f9f20ce6d5d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697120"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Passo a passo: Publicar uma extensão do Visual Studio via linha de comando

Este passo a passo mostra como publicar uma extensão do Visual Studio no Visual Studio Marketplace usando a linha de comando. Quando você adiciona sua extensão ao Marketplace, os desenvolvedores podem usar a caixa de diálogo [**Extensões e Atualizações**](../ide/finding-and-using-visual-studio-extensions.md) para navegar por extensões novas e atualizadas.

VsixPublisher.exe é a ferramenta de linha de comando para publicar extensões do Visual Studio no Marketplace. Ele pode ser acessado a partir de ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. Os comandos disponíveis nesta ferramenta são: **publicar,** **criarPublisher,** **excluirPublisher,** **excluirExtensão,** **login,** **logout**.

## <a name="commands"></a>Comandos

### <a name="publish"></a>Publicar

Publica uma extensão para o Marketplace. A extensão pode ser um vsix, um arquivo exe/msi ou um link. Se a extensão já existir com a mesma versão, ela substituirá a extensão. Se a extensão ainda não existir, criará uma nova extensão.

|Opções de comando |Descrição |
|---------|---------|
|carga útil (necessária) | Ou um caminho para a carga útil a ser publicada ou um link para usar como "URL mais informações". |
|publicarManifesto (obrigatório) | Caminho para o arquivo manifesto de publicação para usar. |
|ignorar avisos | Lista de avisos a ignorar ao publicar uma extensão. Esses avisos são mostrados como mensagens de linha de comando ao publicar uma extensão. (por exemplo, "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Pat (Personal Access Token, token de acesso pessoal) usado para autenticar o editor. Caso não seja fornecido, o PAT é adquirido dos usuários conectados. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>Createpublisher

Cria um editor no Marketplace. Também registra o editor na máquina para ações futuras (por exemplo, excluindo/publicando uma extensão).

|Opções de comando |Descrição |
|---------|---------|
|displayName (obrigatório) | Nome de exibição do editor. |
|editorName (obrigatório) | O nome do editor (por exemplo, o identificador). |
|personalAccessToken (obrigatório) | Token de acesso pessoal que é usado para autenticar o editor. |
|shortDescription | Uma breve descrição do editor (não um arquivo). |
|Longdescription | Uma longa descrição do editor (não um arquivo). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>excluirEditor

Exclui um editor no Marketplace.

|Opções de comando |Descrição |
|---------|---------|
|editorName (obrigatório) | O nome do editor (por exemplo, o identificador). |
|personalAccessToken (obrigatório) | Token de acesso pessoal que é usado para autenticar o editor. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>excluirExtensão

Exclui uma extensão do Marketplace.

|Opções de comando |Descrição |
|---------|---------|
|extensãoNome (obrigatório) | O nome da extensão para excluir. |
|editorName (obrigatório) | O nome do editor (por exemplo, o identificador). |
|personalAccessToken | Token de acesso pessoal que é usado para autenticar o editor. Se não for fornecido, o pat é adquirido dos usuários conectados. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>login

Registra um editor na máquina.

|Opções de comando |Descrição |
|---------|---------|
|personalAccessToken (obrigatório | Token de acesso pessoal que é usado para autenticar o editor. |
|editorName (obrigatório) | O nome do editor (por exemplo, o identificador). |
|substituir | Especifica que qualquer editor existente deve ser substituído com o novo token de acesso pessoal. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Tire um editor da máquina.

|Opções de comando |Descrição |
|---------|---------|
|editorName (obrigatório) | O nome do editor (por exemplo, o identificador). |
|ignorarMissingEditor | Especifica que a ferramenta não deve errar se o editor especificado ainda não estiver logado. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>publicarArquivo Manifest

Um arquivo publishManifest é usado pelo comando **publish.** Ele representa todos os metadados sobre a extensão que o Marketplace precisa saber. Se a extensão que está sendo carregada for de uma extensão VSIX, a propriedade "identidade" só deve ter o conjunto "internalName". Isso porque o resto das propriedades de "identidade" podem ser geradas a partir do arquivo vsixmanifest. Se a extensão for um msi/exe ou uma extensão de link, o usuário deverá fornecer os campos necessários na propriedade "identidade". O restante do manifesto contém informações específicas para o Marketplace (por exemplo, categorias, se Q&A está habilitado, etc.).

A extensão VSIX publica amostra de arquivo Manifesto:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

MSI/EXE ou LINK publicam amostra de arquivo Manifesto:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>Arquivos de ativos

Arquivos de ativos podem ser fornecidos para incorporar coisas como imagens no arquivo readme. Por exemplo, se uma extensão tiver o seguinte documento de "visão geral" markdown:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Para resolver "images/testlogo.png" no exemplo anterior, um usuário pode fornecer "assetFiles" em seu manifesto de publicação como abaixo:

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>Passo a passo da publicação

### <a name="prerequisites"></a>Pré-requisitos

Para acompanhar este passo a passo, você deve instalar o Visual Studio SDK. Para obter mais informações, consulte [Instalando o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Crie uma extensão do Visual Studio

Neste caso, usaremos uma extensão VSPackage padrão, mas as mesmas etapas são válidas para todo tipo de extensão.

1. Crie um VSPackage em C# chamado "TestPublish" que tenha um comando de menu. Para obter mais informações, consulte [Criando sua Primeira Extensão: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Empacotar sua extensão

1. Atualize a extensão vsixmanifest com as informações corretas sobre nome do produto, autor e versão.

   ![atualizar extensão vsixmanifest](media/update-extension-vsixmanifest.png)

2. Construa sua extensão no modo **de liberação.** Agora, sua extensão será embalada como um VSIX na pasta \bin\Release.

3. Você pode clicar duas vezes no VSIX para verificar a instalação.

### <a name="test-the-extension"></a>Teste a extensão

 Antes de distribuir a extensão, construa e teste-a para ter certeza de que ela está instalada corretamente na instância experimental do Visual Studio.

1. No Visual Studio, comece a depurar. para abrir uma instância experimental do Visual Studio.

2. Na instância experimental, vá para o menu **Ferramentas** e clique **em Extensões e Atualizações...**. A extensão TestPublish deve aparecer no painel central e ser ativada.

3. No menu **Ferramentas,** certifique-se de ver o comando de teste.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Publique a extensão para o Marketplace via linha de comando

1. Certifique-se de que você construiu a versão de versão de sua extensão e que ela está atualizada.

2. Certifique-se de ter criado arquivos publishmanifest.json e overview.md.

3. Abra a linha de comando e navegue até ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\.

4. Para criar um novo editor, use o seguinte comando:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Na criação bem-sucedida do publisher, você verá a seguinte mensagem de linha de comando:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Você pode verificar o novo editor que você criou navegando para [o Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Para publicar uma nova extensão, use o seguinte comando:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Na criação bem-sucedida do publisher, você verá a seguinte mensagem de linha de comando:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Você pode verificar a nova extensão que você publicou navegando para [o Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Instale a extensão do Visual Studio Marketplace

Agora que a extensão foi publicada, instale-a no Visual Studio e teste-a lá.

1. No Visual Studio, no menu **Ferramentas,** clique em **Extensões e Atualizações...**.

2. Clique **em Online** e, em seguida, procure por TestPublish.

3. Clique em **Download**. Em seguida, a prorrogação será agendada para instalação.

4. Para concluir a instalação, feche todas as instâncias do Visual Studio.

## <a name="remove-the-extension"></a>Remover a extensão

Você pode remover a extensão do Visual Studio Marketplace e do seu computador.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Para remover a extensão do Marketplace via linha de comando

1. Se você quiser remover uma extensão, use o seguinte comando:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Na exclusão bem-sucedida da extensão, você verá a seguinte mensagem de linha de comando:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Para remover a extensão do seu computador

1. No Visual Studio, no menu **Ferramentas,** clique em **Extensões e Atualizações**.

2. Selecione "MyVsixExtension" e clique em **Desinstalar**. Em seguida, a prorrogação será programada para desinstalação.

3. Para concluir a desinstalação, feche todas as instâncias do Visual Studio.
