---
title: 'Como: Migrar Projetos de Extensibilidade para o Visual Studio 2017 | Microsoft Docs'
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b0cae0261b185ee08400e5f3d25735634663f54a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710988"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Como: Migrar projetos de extensibilidade para o Visual Studio 2017

Este documento explica como atualizar projetos de extensibilidade para o Visual Studio 2017. Além de descrever como atualizar os arquivos do projeto, ele também descreve como atualizar da versão 2 do manifesto de extensão (VSIX v2) para o novo formato manifesto VSIX da versão 3 (VSIX v3).

## <a name="install-visual-studio-2017-with-required-workloads"></a>Instale o Visual Studio 2017 com cargas de trabalho necessárias

Certifique-se de que sua instalação inclua as seguintes cargas de trabalho:

* Desenvolvimento de área de trabalho do .NET
* Desenvolvimento de extensões do Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Abra a solução VSIX no Visual Studio 2017

Todos os projetos VSIX exigirão uma grande versão de atualização unidirecional para o Visual Studio 2017.

O arquivo do projeto (por exemplo **.csproj*) será atualizado:

* MinimumVisualStudioVersion - agora definido como 15.0
* OldToolsVersion (se antes existe) - agora definido como 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Atualize o pacote Microsoft.VSSDK.BuildTools NuGet

> [!Note]
> Se sua solução não fizer referência ao pacote Microsoft.VSSDK.BuildTools NuGet, você pode pular essa etapa.

Para construir sua extensão no novo formato VSIX v3 (versão 3), sua solução precisará ser construída com as novas Ferramentas de Compilação VSSDK. Isso será instalado com o Visual Studio 2017, mas sua extensão VSIX v2 pode estar segurando uma referência a uma versão mais antiga via NuGet. Se assim for, você precisará instalar manualmente uma atualização do pacote Microsoft.VSSDK.BuildTools NuGet para sua solução.

Para atualizar as referências do NuGet ao Microsoft.VSSDK.BuildTools:

* Clique com o botão direito do mouse na solução e escolha **Gerenciar pacotes NuGet para solução**.
* Navegue até a guia **Atualizações.**
* Selecione **Microsoft.VSSDK.BuildTools (versão mais recente)**.
* **Atualização de imprensa**.

![Ferramentas de compilação DO VSSDK](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Faça alterações no manifesto de extensão VSIX

Para garantir que a instalação do Visual Studio pelo usuário tenha todos os conjuntos necessários para executar a extensão, especifique todos os componentes ou pacotes pré-requisitos no arquivo manifesto de extensão. Quando um usuário tenta instalar a extensão, o VSIXInstaller verificará se todos os pré-requisitos estão instalados. Se alguns estiverem faltando, o usuário será solicitado a instalar os componentes ausentes como parte do processo de instalação da extensão.

> [!Note]
> No mínimo, todas as extensões devem especificar o componente do editor principal do Visual Studio como pré-requisito.

* Editar o arquivo manifesto de extensão (geralmente chamado *de source.extension.vsixmanifest*).
* Certifique-se `InstallationTarget` de incluir 15.0.
* Adicione os pré-requisitos de instalação necessários (como mostrado no exemplo abaixo).
  * Recomendamos que você especifique apenas IDs de componentes para pré-requisitos de instalação.
  * Consulte a seção no final deste documento para obter [instruções sobre a identificação de identidades de componentes](#find-component-ids).

Exemplo:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opção: Use o designer para fazer alterações no manifesto de extensão VSIX

Em vez de editar diretamente o Manifesto XML, você pode usar a nova guia **Pré-requisitos** no Manifest Designer para selecionar os pré-requisitos e o XML será atualizado para você.

> [!Note]
> O Manifest Designer só permitirá selecionar componentes (não cargas de trabalho ou pacotes) que estão instalados na instância atual do Visual Studio. Se você precisar adicionar um pré-requisito para uma carga de trabalho, pacote ou componente que não esteja instalado no momento, edite o manifesto XML diretamente.

* Arquivo Open *source.extension.vsixmanifest [Design].*
* Selecione a guia **Pré-requisitos** e pressione **Novo** botão.

   ![VSIX manifest designer](media/vsix-manifest-designer.png)

* A **janela Adicionar novo pré-requisito** será aberta.

   ![adicionar vsix pré-requisito](media/add-vsix-prerequisite.png)

* Clique no menu de entrada para **Nome** e selecione o pré-requisito desejado.
* Atualize a versão se necessário.

   > [!Note]
   > O campo de versão será pré-preenchido com a versão do componente atualmente instalado, com um intervalo que abrange até (mas não incluindo) a próxima versão principal do componente.

   ![adicionar pré-requisito roslyn](media/add-roslyn-prerequisite.png)

* Pressione **OK**.

## <a name="update-debug-settings-for-the-project"></a>Atualizar configurações de depuração para o projeto

Se você deseja depurar sua extensão em uma instância experimental do Visual Studio, certifique-se de que as configurações do projeto para**a ação** **Debug** > Start têm o programa externo **Iniciar:** valor definido para o arquivo *devenv.exe* da instalação do Visual Studio 2017.

Pode parecer: *C:\Arquivos de programa (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe*

![iniciar programa externo](media/start-external-program.png)

> [!Note]
> O Debug Start Action é normalmente armazenado no arquivo *.csproj.user.* Este arquivo geralmente é incluído no arquivo *.gitignore* e, portanto, normalmente não é salvo com outros arquivos de projeto quando comprometido com o controle de origem. Como tal, se você tiver retirado sua solução fresca do controle de origem, é provável que o projeto não tenha valores definidos para Iniciar ação. Novos projetos VSIX criados com o Visual Studio 2017 terão um arquivo *.csproj.user* criado com padrões apontando para o diretório de instalação do Visual Studio atual. No entanto, se você estiver migrando uma extensão VSIX v2, é provável que o arquivo *.csproj.user* contenha referências ao diretório de instalação da versão anterior do Visual Studio. Definir o valor para**a ação** **Debug** > Start permitirá que a instância experimental do Visual Studio correta seja lançada quando você tentar depurar sua extensão.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Verifique se a extensão é construída corretamente (como um VSIX v3)

* Construa o projeto VSIX.
* Descompacte o VSIX gerado.
  * Por padrão, o arquivo VSIX vive dentro *do bin/Debug* ou *bin/Release* como *[YourCustomExtension].vsix*.
  * Renomeie *.vsix* para *.zip* para visualizar facilmente o conteúdo.
* Verifique a existência de três arquivos:
  * *extensão.vsixmanifest*
  * *manifest.json*
  * *catálogo.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>Verifique quando todos os pré-requisitos necessários são instalados

Teste que o VSIX instala com sucesso em uma máquina com todos os pré-requisitos necessários instalados.

> [!Note]
> Antes de instalar qualquer extensão, desligue todas as instâncias do Visual Studio.

Tente instalar a extensão:

* No Visual Studio 2017

![Instalador VSIX no Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Opcional: Confira as versões anteriores do Visual Studio.
  * Prova a retrocompatibilidade.
  * Deve trabalhar para o Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Opcional: Verifique se o Verificador de Versão do Instalador VSIX oferece uma escolha de versões.
  * Inclui versões anteriores do Visual Studio (se instalado).
  * Inclui o Visual Studio 2017.

Se o Visual Studio foi aberto recentemente, você pode ver uma caixa de diálogo como esta:

![vs processos em execução](media/vs-running-processes.png)

Aguarde que os processos sejam encerrados ou termine manualmente as tarefas. Você pode encontrar os processos pelo nome listado ou com o PID listado entre parênteses.

> [!Note]
> Esses processos não serão desligados automaticamente enquanto uma instância do Visual Studio estiver sendo executado. Certifique-se de que você desligou todas as instâncias do Visual Studio na máquina - incluindo as de outros usuários, e então continue a tentar novamente.

## <a name="check-when-missing-the-required-prerequisites"></a>Verifique se faltam os pré-requisitos necessários

* Tente instalar a extensão em uma máquina com o Visual Studio 2017 que NÃO CONTENHA todos os componentes definidos nos Pré-requisitos (acima).
* Verifique se a instalação identifica o componente/s ausente e lista-os como um pré-requisito no VSIXInstaller.
* Nota: A elevação será necessária se algum pré-requisito precisar ser instalado com a extensão.

![vsixinstaller faltando pré-requisito](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>Decida sobre os componentes

Ao procurar suas dependências, você verá que uma dependência pode mapear para vários componentes. Para determinar quais dependências você deve especificar como seu pré-requisito, sugerimos que você escolha um componente que tenha uma funcionalidade semelhante à sua extensão e também considere seus usuários e que tipo de componentes eles provavelmente teriam instalado ou não se importaria min. Também sugerimos a construção de suas extensões de uma maneira onde os pré-requisitos necessários satisfaçam apenas o mínimo que permitirá que sua extensão seja executada e para recursos adicionais eles fiquem dormentes se certos componentes não forem detectados.

Para fornecer mais orientações, identificamos alguns tipos de extensão comuns e seus pré-requisitos sugeridos:

Tipo de extensão | Nome de exibição | ID
--- | --- | ---
Editor | Editor do Visual Studio Core | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# e Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Núcleo da carga de trabalho de área de trabalho gerenciada | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Depurador | Depurador Just-In-Time | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>Encontre iDs de componentes

A lista de componentes classificados pelo produto Visual Studio está na [carga de trabalho visual studio 2017 e IDs de componentes](/visualstudio/install/workload-and-component-ids?view=vs-2019). Use esses IDs componentes para seus IDs pré-requisitos em seu manifesto.

Se você não tiver certeza de qual componente contém um binário específico, baixe a [planilha de mapeamento binário Component ->](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Existem quatro colunas na folha excel: **Component Name**, **ComponentId**, **Version**e **Binary /File Names**.  Você pode usar os filtros para pesquisar e encontrar componentes e binários específicos.

Para todas as suas referências, primeiro determine quais estão no componente do editor principal (Microsoft.VisualStudio.Component.CoreEditor).  No mínimo, exigimos que o componente do editor principal seja especificado como um pré-requisito para todas as extensões. Das referências que restam que não estão no editor principal, adicione filtros na seção **Binários /Nomes de Arquivos** para encontrar componentes que tenham qualquer um dos subconjuntos dessas referências.

Exemplos:

* Se você tiver uma extensão de depurador e souber que seu projeto tem uma referência ao *VSDebugEng.dll* e *ao VSDebug.dll,* clique no botão de filtro no cabeçalho **Binaries / Files Names.**  Procure por "VSDebugEng.dll" e selecione *OK*.  Clique no botão de filtro no **cabeçalho Binaries / Files Names** novamente e procure por "VSDebug.dll".  Selecione a caixa de seleção **Adicionar seleção atual para filtrar** e selecionar **OK**.  Agora procure através do **Nome do Componente** para encontrar um componente mais relacionado ao seu tipo de extensão. Neste exemplo, você escolheria o depurador Just-In-Time e adicioná-lo ao seu vsixmanifest.
* Se você sabe que seu projeto lida com elementos dedepurador, você pode pesquisar em "depurador" na caixa de pesquisa do filtro para ver quais componentes contêm depurador em seu nome.

## <a name="specify-a-visual-studio-2017-release"></a>Especificar uma versão do Visual Studio 2017

Se sua extensão exigir uma versão específica do Visual Studio 2017, por exemplo, ela depende de um recurso lançado em 15.3, você deve especificar o número de compilação em seu VSIX **InstallationTarget**. Por exemplo, a versão 15.3 tem um número de compilação de '15.0.26730.3'. Você pode ver o mapeamento de lançamentos para construir números [aqui.](../install/visual-studio-build-numbers-and-release-dates.md) O uso do número de versão '15.3' não funcionará corretamente.

Se a sua extensão exigir 15,3 ou mais, você declararia a **Versão De Destino de Instalação** como [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
