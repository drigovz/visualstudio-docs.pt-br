---
title: Comando ShowWebBrowser
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f6d8249503ed775d584c913d685ae35473134be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62950638"
---
# <a name="showwebbrowser-command"></a>Comando ShowWebBrowser

Exibe a URL especificada em uma janela de navegador da Web, tanto dentro do IDE (ambiente de desenvolvimento integrado) ou externa ao IDE.

## <a name="syntax"></a>Sintaxe

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Arguments
 `URL`

 Necessário. URL (Uniform Resource Locator) do site da Web.

## <a name="switches"></a>Opções
 /new

 Opcional. Especifica que a página é exibida em uma nova instância do navegador da Web.

 /ext

 Opcional. Especifica que a página é exibida no navegador da Web padrão fora do IDE.

## <a name="remarks"></a>Comentários
 O alias do comando **ShowWebBrowser** é **navegue** ou **nav**.

## <a name="example"></a>Exemplo
 O exemplo a seguir exibe a home page do Microsoft Docs em um navegador da Web fora do IDE. Se uma instância do navegador da Web já estiver aberta, ela será usada; caso contrário, uma nova instância será iniciada.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>Consulte também

- [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Janela Comando](../../ide/reference/command-window.md)
- [Caixa Localizar/Comando](../../ide/find-command-box.md)
- [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)