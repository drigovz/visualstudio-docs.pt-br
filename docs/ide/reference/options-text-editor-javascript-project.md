---
title: Opções, Editor de Texto, JavaScript, Projeto
ms.date: 1/15/2019
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 190cbdb2a8096415985d83fc525b997572d252c2
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605924"
---
# <a name="options-text-editor-javascript-project"></a>Opções, Editor de Texto, JavaScript, Projeto

Use a página **Projeto** da caixa de diálogo **Opções** para especificar opções de projeto JavaScript e TypeScript no Editor de Código. Para acessar essa página, na barra de menus, escolha **Ferramentas** > **Opções** e expanda **Editor de Texto** > **JavaScript/TypeScript** > **Projeto**.

## <a name="project-analysis-options"></a>Opções de análise do projeto

Essas opções determinam como o editor analisa os projetos, relata diagnósticos e sugere melhorias. Marque ou desmarque as opções para especificar como o editor lida com essas situações.

### <a name="uielement-list"></a>Lista UIElement

- **Analisar apenas os projetos que contêm arquivos abertos no editor**
- **Reportar apenas os diagnósticos para arquivos abertos no editor**
- **Sugerir possíveis aprimoramentos que não são correções**

## <a name="virtual-projects-in-solution-explorer"></a>Projetos virtuais no Gerenciador de Soluções

Essas opções permitem que você escolha se deseja exibir Projetos Virtuais quando uma Solução é carregada ou não carregada.

## <a name="compile-on-save"></a>Compilar ao salvar

Essas opções determinam se os arquivos TypeScript que não fazem parte do projeto são compilados automaticamente. Marque a caixa de seleção e, em seguida, escolha o tipo de geração de código a ser usado.

### <a name="uielement-list"></a>Lista UIElement

- **Usar geração de código do AMD para módulos que não fazem parte de um projeto**
- **Usar geração de código CommonJS para módulos que não fazem parte de um projeto**
- **Usar geração de código UMD para módulos que não fazem parte de um projeto**
- **Usar geração de código do Sistema para módulos que não fazem parte de um projeto**
- **Usar geração de código ES2015 para módulos que não fazem parte de um projeto**

## <a name="ecmascript-version-for-files-that-are-not-part-of-a-project"></a>Versão ECMAScript para arquivo que não fazem parte de um projeto

Essas opções permitem que você selecione a versão do ECMAScript para arquivos que não fazem parte de um projeto. Você pode escolher entre **ECMAScript 3**, **ECMAScript 5** ou **ECMAScript 6**.

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>Emissão JSX para arquivos TSX que não fazem parte de um projeto

Essas opções determinam como o editor trata arquivos TypeScript que não fazem parte de um projeto.

### <a name="uielement-list"></a>Lista UIElement

|Opção|DESCRIÇÃO|
|------------|-----------------|
|**React Framework**|Quando essa opção estiver selecionada, o Editor de Códigos emitirá uma extensão de arquivo *.js*.|
|**Preserve**|Quando essa opção estiver selecionada, o Editor de Códigos manterá o JSX como parte da saída e emitirá uma extensão de arquivo *.jsx*.|

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)