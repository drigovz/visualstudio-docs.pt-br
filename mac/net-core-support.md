---
title: Suporte do .NET Core
description: Este documento aborda o suporte de versões do .NET Core no Visual Studio para Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 01/08/2020
ms.assetid: 8B8CEBE8-00DA-4AD1-8193-77F58B57F244
ms.openlocfilehash: b9892a322c0264a1bdb68d672c7fe6c6e9b08d4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84183594"
---
# <a name="net-core-support"></a>Suporte do .NET Core

A tabela a seguir descreve as versões do .NET Core compatíveis com as versões prévias e estáveis do Visual Studio para Mac:

| Versão do SDK do .NET Core |Visual Studio para Mac 8,1 | Visual Studio para Mac 8,2 | Visual Studio para Mac 8,3 | Visual Studio para Mac 8,4 | Visual Studio para Mac 8,5 | Visual Studio para Mac 8,6 |
|---------|---------|---------|---------|---------|---------|---------|
|v2.1.0 - v2.1.5xx | | | | | | |
|v2.1.600 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v2.2.1 - v2.2.1xx | | | | | | |
|v2.2.200 + |✔︎|✔︎|✔︎|✔︎|✔︎|✔︎|
|v3.0 | | |✔︎|✔︎|✔︎|✔︎|
|v3.1 | | | |✔︎|✔︎|✔︎|
|v 5.0 (versão prévia) | | | | | |✔︎|

> [!IMPORTANT]
> Não há suporte para versões de visualização do SDK do .NET Core; Atualize para a versão de lançamento. Ao instalar o Visual Studio para Mac 8,4, a versão de lançamento do .NET Core v 3.1 será instalada.

> [!IMPORTANT]
> Se você estava usando o .NET Core v2.2.1xx com o Visual Studio para Mac 8.0, será necessário atualizar manualmente para uma versão compatível do .NET Core, conforme listado na tabela acima. Recomendamos o [2.1.700](https://dotnet.microsoft.com/download/dotnet-core/2.1) ou o [2.2.300](https://dotnet.microsoft.com/download/dotnet-core/2.2)

* O .NET Core v 3.1 é instalado por padrão para 8,4, 8,5 e 8,6.
* O .NET Core v 3.0 é instalado por padrão para 8,3.
* O .NET Core v2.1.701 (v2.1.700 para 8.1) é instalado por padrão com o instalador.
* Para baixar qualquer outra versão do .NET Core, visite a [página dotnet](https://dotnet.microsoft.com/download/dotnet-core).
* Ao usar o .NET Core 3,0, a versão 8 do C# será usada por padrão. O C# 7,3 é o padrão ao usar o .NET Core 2. x. Consulte [controle de versão da linguagem C#](/dotnet/csharp/language-reference/configure-language-version) para obter mais informações.
* Para saber mais sobre como instalar uma versão prévia do Visual Studio para Mac, confira o guia [Instalar uma versão prévia](/visualstudio/mac/install-preview).
