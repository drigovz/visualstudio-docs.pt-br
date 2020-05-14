---
title: Criando modelos personalizados de projetos e itens | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae404004f2660048ef7581a661d8f785495ed95a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739457"
---
# <a name="create-custom-project-and-item-templates"></a>Crie modelos personalizados de projetos e itens

O Visual Studio SDK inclui modelos de projeto que criam um modelo de projeto personalizado e um modelo de item personalizado. Esses modelos incluem algumas substituições comuns de parâmetros e constroem como arquivos zip. Eles não são implantados automaticamente e não estão disponíveis na instância experimental. Você deve copiar o arquivo zip gerado para o diretório do modelo do usuário.

Os modelos de criação de modelos permitem incluir modelos em extensões maiores. Isso permite implementar o controle de versão nos arquivos de origem e construir um grupo de projetos de modelo em um pacote VSIX.

Você também pode configurar um modelo para instalar pacotes NuGet. Para obter mais informações, consulte [os pacotes NuGet nos modelos do Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates).

Para cenários básicos de criação de modelos, você deve usar o assistente **Modelo de exportação,** que é desfeita para um arquivo compactado. Para obter mais informações sobre a criação de modelos básicos, consulte [Criar modelos de projeto e itens](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> A partir do Visual Studio 2017, a digitalização para modelos personalizados de projetos e itens não será mais realizada. Em vez disso, a extensão deve fornecer arquivos manifestos de modelo que descrevem a localização de instalação desses modelos. Você pode usar o Visual Studio 2017 para atualizar suas extensões VSIX. Se você implantar sua extensão usando um MSI, você deve gerar os arquivos manifestos de modelo manualmente. Para obter mais informações, consulte [Atualizar modelos personalizados de projeto e itens para o Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). O esquema de manifesto de modelo está documentado no [modelo visual studio manifesta referência de esquema](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Criar um modelo de projeto

1. Crie um projeto de modelo de projeto. Você pode encontrar o modelo de projeto na caixa de diálogo **Novo Projeto,** procurando por "modelo de projeto" e selecionando a versão C# ou Visual Basic.

     O modelo gera um arquivo de classe, um ícone, um arquivo *.vstemplate,* um arquivo de projeto editável chamado *ProjectTemplate.vbproj* ou *ProjectTemplate.csproj*, e alguns arquivos que são normalmente gerados por outros tipos de projeto, como um arquivo *resources.resx,* um arquivo *AssemblyInfo* e um arquivo *.settings.* Cada arquivo de código contém substituições comuns de parâmetros, quando apropriado.

![seleção de projeto modelo de projeto](media/project-template-selection.png)

2. Adicione e remova itens do projeto conforme necessário para o seu projeto. Não remova o arquivo de projeto editável, o arquivo *AssemblyInfo* ou o arquivo *.vstemplate.*

3. Atualize o arquivo *.vstemplate* para refletir quaisquer adições e exclusões. O elemento [Projeto](../extensibility/project-element-visual-studio-templates.md) deve conter um elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) para cada arquivo a ser incluído no modelo.

4. Modifique seus arquivos de código e outros conteúdos voltados para o usuário e adicione substituições de parâmetros apropriadas.

5. Modifique o conteúdo gerado conforme necessário.

6. Compile o projeto.

     O Visual Studio cria um arquivo *.zip* que contém seu modelo. Ele não é implantado e não está disponível na instância experimental.

## <a name="create-an-item-template"></a>Criar um modelo de item

1. Crie um projeto de modelo de item.

     O modelo gera um arquivo de classe, um ícone, um arquivo *.vstemplate* e um arquivo *AssemblyInfo.* O arquivo de classe contém algumas substituições comuns de parâmetros.

2. Adicione e remova itens do projeto conforme necessário para o seu projeto.

3. Atualize o arquivo *.vstemplate* para refletir quaisquer adições e exclusões. O elemento [Projeto](../extensibility/project-element-visual-studio-templates.md) deve conter um elemento [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) para cada arquivo a ser incluído no modelo.

4. Modifique seus arquivos de código e outros conteúdos voltados para o usuário e adicione substituições de parâmetros apropriadas.

5. Modifique o conteúdo gerado conforme necessário.

6. Compile o projeto.

     O Visual Studio cria um arquivo compactado que contém seu modelo. Ele não é implantado e não está disponível na instância experimental.

## <a name="deployment"></a>Implantação

### <a name="to-deploy-the-project-or-item-template"></a>Para implantar o modelo de projeto ou item

1. Crie um projeto VSIX. Para obter mais informações, consulte [o modelo do projeto VSIX](../extensibility/vsix-project-template.md).

2. Defina o projeto VSIX como o projeto de startup. No **Solution Explorer,** selecione o nó do projeto VSIX, clique com o botão direito do mouse e selecione **Definir como Projeto de Inicialização**.

3. Defina o projeto do modelo de projeto como um ativo do projeto VSIX. Abra o arquivo *.vsixmanifest.* Vá para a guia **Ativos** e clique em **Novo**.

    1. Defina o **campo Tipo** para **Microsoft.VisualStudio.ProjectTemplate** ou **Microsoft.VisualStudio.ItemTemplate**.

    2. Para obter, selecione o projeto A na opção **de solução atual** e selecione o projeto que contém seu modelo.

4. Construa a solução e pressione **F5**. A instância experimental aparece.

5. Para um projeto de modelo de projeto, você deve ver o modelo de projeto listado na caixa de diálogo **Novo Projeto** **(Projeto****arquivo** > **novo),** > no nó Visual C# ou Visual Basic. Para um projeto de modelo de item, você deve ver o modelo de item listado na caixa de diálogo **Adicionar novo item.** Para exibir a caixa de diálogo **Adicionar novo item,** no **Solution Explorer,** selecione o nó do projeto e clique **em Adicionar** > **novo item**).

## <a name="see-also"></a>Confira também

- [Referência de modelo do Visual Studio](../ide/creating-project-and-item-templates.md)
- [Pacotes NuGet em modelos do Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
