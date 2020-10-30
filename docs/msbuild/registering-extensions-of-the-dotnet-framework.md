---
title: Registrando extensões do .NET Framework | Microsoft Docs
description: Saiba como adicionar uma pasta que contém um assembly que estende uma versão específica do .NET Framework ao registro do sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d63dda9cab50474fd357043d5f694a645a18b2b9
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048757"
---
# <a name="register-extensions-of-the-net-framework"></a>Registrar extensões do .NET Framework

Você pode desenvolver um assembly que estende uma versão específica do .NET Framework. Para habilitar o assembly a ser exibido na caixa de diálogo **Adicionar Referências** do Visual Studio, você deve adicionar a pasta que contém o Registro do sistema.

 Por exemplo, suponha que a empresa Trey Research desenvolveu uma biblioteca que estende o .NET Framework 4 e deseja que os assemblies de biblioteca apareçam na caixa de diálogo **Adicionar Referências** quando um projeto for voltado para o .NET Framework 4. Suponha também que os assemblies são de 32 bits em execução em um computador de 32 bits ou assemblies de 64 bits que são executados em um computador de 64 bits e que eles serão instalados na pasta *C:\TreyResearch\Extensions4\\* .

 Registre essa pasta usando essa chave: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\** . Forneça o seguinte valor padrão para a chave: **C:\TreyResearch\Extensions4** .

> [!NOTE]
> O número de build da versão do .NET Framework pode ser diferente.

 Para registrar um assembly de 32 bits em um computador de 64 bits, use o nó Wow6432, por exemplo: **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\** .

### <a name="see-also"></a>Veja também

- [integração com o Visual Studio](../msbuild/visual-studio-integration-msbuild.md)
