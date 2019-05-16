---
title: Classes específicas de cultura para Windows Forms e Web Forms globais | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e18cda54431eec580464ccb59c5c6b6cce87d225
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65701123"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Classes específicas de cultura para Windows Forms e Web Forms globais
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cada cultura tem diferentes convenções para exibir datas, hora, números, moeda e outras informações. O namespace <xref:System.Globalization> contém classes que podem ser usadas para modificar o modo como os valores específicos de cultura são exibidos, como <xref:System.Globalization.DateTimeFormatInfo>, **Calendário** e <xref:System.Globalization.NumberFormatInfo>.  
  
## <a name="using-the-culture-setting"></a>Usando a configuração de cultura  
 Mas, na maioria das vezes, você usará a configuração de cultura armazenada no aplicativo ou no painel de controle **Opções Regionais** para determinar automaticamente as convenções no tempo de execução e formatar as informações adequadamente. Para obter mais informações sobre como definir a cultura, veja [Como: Definir a cultura e cultura da interface do usuário para globalização dos Windows Forms](https://msdn.microsoft.com/694e049f-0b91-474a-9789-d35124f248f0) ou [como: Definir a cultura e cultura da interface do usuário para globalização de página da Web do ASP.NET](https://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0). As classes que formatam informações automaticamente de acordo com a configuração de cultura são chamadas classes específicas de cultura. Alguns métodos específicos de cultura são <xref:System.IFormattable.ToString%2A?displayProperty=fullName>, <xref:System.Console.WriteLine%2A?displayProperty=fullName> e <xref:System.String.Format%2A?displayProperty=fullName>. Algumas funções específicas de cultura (na linguagem do Visual Basic) são `MonthName` e `WeekDayName`.  
  
 Por exemplo, o código a seguir mostra como você pode usar o método <xref:System.IFormattable.ToString%2A> para formatar a moeda para a cultura atual:  
  
```vb  
' Put the Imports statements at the beginning of the code module  
Imports System.Threading  
Imports System.Globalization  
' Display a number with the culture-specific currency formatting  
Dim MyInt As Integer = 100  
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))  
  
```  
  
```csharp  
// Put the using statements at the beginning of the code module  
using System.Threading;  
using System.Globalization;  
// Display a number with the culture-specific currency formatting  
int myInt = 100;  
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));  
```  
  
 Se a cultura for definida como "fr-FR", você verá isto na janela de saída:  
  
 `100,00`  
  
 Se a cultura for definida como "en-US", você verá isto na janela de saída:  
  
 `$100.00`  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName>   
 <xref:System.Globalization.DateTimeFormatInfo>   
 <xref:System.Globalization.NumberFormatInfo>   
 <xref:System.Globalization.Calendar>   
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>   
 <xref:System.String.Format%2A?displayProperty=fullName>   
 [Globalizando e localizando aplicativos](../ide/globalizing-and-localizing-applications.md)
