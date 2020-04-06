---
title: Migrando um serviço de idioma legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e2eff3f3a27b7d8a276c8ed776c1e11d5ce332e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707109"
---
# <a name="migrating-a-legacy-language-service"></a>Migrando um serviço de linguagem herdado
Você pode migrar um serviço de idioma legado para uma versão posterior do Visual Studio atualizando o projeto e adicionando um arquivo source.extension.vsixmanifest ao projeto. O serviço de idiomas em si continuará funcionando como antes, porque o editor do Visual Studio o adapta.

 Os serviços de linguagem legados são implementados como parte de um VSPackage, mas a maneira mais nova de implementar recursos de serviço de idioma é usar extensões MEF. Para saber mais sobre a nova maneira de implementar um serviço de idiomas, consulte [Editor e Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Recomendamos que você comece a usar a Nova API do editor o mais rápido possível. Isso melhorará o desempenho do seu serviço de idiomas e permitirá que você aproveite os novos recursos do editor.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrando uma solução de serviço de linguagem visual studio 2008 para uma versão posterior
 As etapas a seguir mostram como adaptar uma amostra do Visual Studio 2008 chamada RegExLanguageService. Você pode encontrar essa amostra em uma instalação do Visual Studio 2008 SDK, no caminho de instalação do *Visual Studio SDK*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\.

> [!IMPORTANT]
> Se o serviço de idioma não definir <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> cores, você deve definir explicitamente `true` no VSPackage:

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Para migrar um serviço de idioma visual studio 2008 para uma versão posterior

1. Instale as versões mais recentes do Visual Studio e do Visual Studio SDK. Para obter mais informações sobre formas de instalar o SDK, consulte [Instalando o Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).

2. Edite o arquivo RegExLangServ.csproj (sem carregá-lo no Visual Studio.

     No `Import` nó que se refere ao arquivo Microsoft.VsSDK.targets, substitua o valor pelo texto a seguir.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Salvar o arquivo e depois fechá-lo.

4. Abra a solução RegExLangServ.sln.

5. A **janela de atualização unidirecional** é exibida. Clique em **OK**.

6. Atualize as propriedades do projeto. Abra a janela Propriedades do **projeto** selecionando o nó do projeto no **Solution Explorer,** clicando com o botão direito do mouse e selecionando **Propriedades**.

    - Na guia **Aplicativo,** altere **a estrutura de destino** para **4.6.1**.

    - Na guia **Debug,** na caixa **Iniciar programa externo,** digite ** \<o caminho de instalação do Visual Studio>\Common7\IDE\devenv.exe.**

         Na caixa **de argumentos da linha comando,** digite/raízesufixo**Exp**.

7. Atualize as seguintes referências:

    - Remova a referência ao Microsoft.VisualStudio.Shell.9.0.dll e adicione referências ao Microsoft.VisualStudio.Shell.14.0.dll e ao Microsoft.VisualStudio.Shell.Immutable.11.0.dll.

    - Remova a referência ao Microsoft.VisualStudio.Package.LanguageService.9.0.dll e adicione uma referência ao Microsoft.VisualStudio.Package.LanguageService.14.0.dll.

    - Adicione uma referência ao Microsoft.VisualStudio.Shell.Interop.10.0.dll.

8. Abra o arquivo VsPkg.cs e `DefaultRegistryRoot` altere o valor do atributo para

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. A amostra original não registra seu serviço de idioma, então você deve adicionar o seguinte atributo ao VsPkg.cs.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Você deve adicionar um arquivo source.extension.vsixmanifest.

    - Copie este arquivo de uma extensão existente para o diretório do projeto. (Uma maneira de obter este arquivo é criar um projeto VSIX (em **Arquivo**, clique em **Novo,** em seguida, clique em **Projeto**. Em Visual Basic ou C# clique **em Extensibility,** depois selecione **Projeto VSIX**.)

    - Adicione o arquivo ao seu projeto.

    - Nas **propriedades**do arquivo, defina **None** **'''''''''Criar', ''''''''''''''''''''''**

    - Abra o arquivo com o **Editor de Manifesto séxion VSIX**.

    - Alterar os seguintes campos:

    - **ID**: RegExLangServ

    - **Nome do produto**: RegExLangServ

    - **Descrição**: Um serviço regular de linguagem de expressão.

    - Em **Ativos,** clique em **Novo,** selecione o **Tipo** para **Microsoft.VisualStudio.VsPackage**, defina a **Fonte** para um projeto na solução atual e, **em**seguida, defina o **Projeto** como **RegExLangServ**.

    - Salve e feche o arquivo.

11. Compile a solução. Os arquivos incorporados são implantados em **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\\\RegExLangServ**.

12. Inicie a depuração. Uma segunda instância do Visual Studio foi aberta.

## <a name="see-also"></a>Confira também
- [Extensibilidade do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-extensibility.md)
