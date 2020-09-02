---
title: Criando modelos de item e de projeto personalizados
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6875e13baa83d349020f50a3fe448a87ec5fd30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197405"
---
# <a name="creating-custom-project-and-item-templates"></a>Criando modelos de item e de projeto personalizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O SDK do Visual Studio inclui modelos de projeto que criam um modelo de projeto personalizado e um modelo de item personalizado. Esses modelos incluem algumas substituições de parâmetro comuns e compilam como arquivos zip. Eles não são implantados automaticamente e não estão disponíveis na instância experimental. Copie o arquivo zip para o local que você

Os modelos de criação de modelo permitem que você inclua modelos em extensões maiores. A inclusão de modelos em extensões permite que você implemente o controle de versão nos arquivos de origem e crie um grupo de projetos de modelo em um pacote VSIX.

Para cenários de criação de modelo básico, você deve usar o assistente para **Exportar modelo** , que gera um arquivo compactado. Para obter mais informações sobre a criação de modelo básico, consulte [criando modelos de projeto e item](../ide/creating-project-and-item-templates.md).

A partir do Visual Studio 2017, a verificação de modelos personalizados de projeto e item não é mais executada. Em vez disso, a extensão deve fornecer arquivos de manifesto de modelo que descrevem o local de instalação desses modelos. Você pode usar a instalação da versão prévia 2 para atualizar suas extensões VSIX. Se você implantar sua extensão usando um MSI, deverá gerar os arquivos de manifesto de modelo manualmente. Para obter mais informações, consulte [upgrade Custom Modelos de Projeto e Item para Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). O esquema de manifesto de modelo está documentado na [referência de esquema de manifesto de modelo do Visual Studio](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).

## <a name="create-a-project-template"></a>Criar um modelo de projeto

1. Crie um projeto de modelo de projeto. Você pode encontrar o modelo de projeto na caixa de diálogo **novo projeto** , na pasta de **extensibilidade** do Visual Basic ou do Visual C#.

     O modelo gera um arquivo de classe, um ícone, um arquivo. vstemplate, um arquivo de projeto editável chamado ProjectTemplate. vbproj ou ProjectTemplate. csproj e alguns arquivos que normalmente são gerados por outros tipos de projeto, como um arquivo. resx de recursos, um arquivo AssemblyInfo e um arquivo. Settings. Cada arquivo de código contém substituições de parâmetro comuns, quando apropriado.

2. Adicione e remova itens do projeto conforme necessário para seu projeto. Não remova o arquivo de projeto editável, o arquivo AssemblyInfo ou o arquivo. vstemplate.

3. Atualize o arquivo. vstemplate para refletir quaisquer inclusões e exclusões. O elemento [Project](../extensibility/project-element-visual-studio-templates.md) deve conter um elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) para cada arquivo a ser incluído no modelo.

4. Modifique seus arquivos de código e outros conteúdos voltados para o usuário e adicione substituições de parâmetro apropriadas.

5. Modifique o conteúdo gerado conforme necessário.

6. Compile o projeto.

     O Visual Studio cria um arquivo. zip que contém o modelo. Ele não é implantado e não está disponível na instância experimental.

## <a name="create-an-item-template"></a>Criar um modelo de item

1. Crie um projeto de modelo de item.

     O modelo gera um arquivo de classe, um ícone, um arquivo. vstemplate e um arquivo AssemblyInfo. O arquivo de classe contém algumas substituições de parâmetro comuns.

2. Adicione e remova itens do projeto conforme necessário para seu projeto.

3. Atualize o arquivo. vstemplate para refletir quaisquer inclusões e exclusões. O elemento [Project](../extensibility/project-element-visual-studio-templates.md) deve conter um elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) para cada arquivo a ser incluído no modelo.

4. Modifique seus arquivos de código e outros conteúdos voltados para o usuário e adicione substituições de parâmetro apropriadas.

5. Modifique o conteúdo gerado conforme necessário.

6. Compile o projeto.

     O Visual Studio cria um arquivo compactado que contém o modelo. Ele não é implantado e não está disponível na instância experimental.

## <a name="deploy-the-project-or-item-template"></a>Implantar o modelo de projeto ou item

1. Crie um projeto VSIX. Para obter mais informações, consulte [modelo de projeto VSIX](../extensibility/vsix-project-template.md).

2. Defina o projeto VSIX como o projeto de inicialização. Na **Gerenciador de soluções**, selecione o nó do projeto VSIX, clique com o botão direito do mouse e selecione **definir como projeto de inicialização**.

3. Defina o projeto de modelo de projeto como um ativo do projeto VSIX. Abra o arquivo. vsixmanifest. Vá para a guia **ativos** e clique em **novo**.

    1. Defina o campo de **tipo** para **Microsoft. VisualStudio. ProjectTemplate** ou **Microsoft. VisualStudio. ItemTemplate**.

    2. Para origem, selecione a opção **um projeto na solução atual** e, em seguida, selecione o projeto que contém o modelo.

4. Compile a solução e pressione F5. A instância experimental é exibida.

5. Para um projeto de modelo de projeto, você deve ver o modelo de projeto listado na caixa de diálogo **novo projeto** (**arquivo/novo/projeto**), no nó Visual C# ou Visual Basic. Para um projeto de modelo de item, você deve ver o modelo de item listado na caixa de diálogo Adicionar novo item (na **Gerenciador de soluções**, selecione o nó do projeto e clique em **Adicionar/novo item**).

## <a name="see-also"></a>Confira também

- [Referência de modelo do Visual Studio](../ide/visual-studio-template-reference.md)