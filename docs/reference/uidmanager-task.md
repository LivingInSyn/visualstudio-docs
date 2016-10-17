---
title: "UidManager Task"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: na
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "UidManager task [WPF MSBuild]"
  - "UidManager task [WPF MSBuild], parameters"
  - "managing UIDs when localizing XAML elements [WPF MSBuild]"
  - "localizing XAML elements [WPF MSBuild], managing UIDs"
  - "checking UIDs when localizing XAML elements [WPF MSBuild]"
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
caps.latest.revision: 5
ms.author: "kempb"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# UidManager Task
The \<xref:Microsoft.Build.Tasks.Windows.UidManager> task checks, updates, or removes unique identifiers (UIDs), in order to localize all [!INCLUDE[TLA#tla_xaml](../reference/includes/tlasharptla_xaml_md.md)] elements that are included in the source [!INCLUDE[TLA2#tla_xaml](../reference/includes/tla2sharptla_xaml_md.md)] files.  
  
## Task Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|`IntermediateDirectory`|Optional **String** parameter.<br /><br /> Specifies the directory that is used to back up the source [!INCLUDE[TLA2#tla_xaml](../reference/includes/tla2sharptla_xaml_md.md)] files that are specified by the **MarkupFiles** parameter.|  
|`MarkupFiles`|Required **ITaskItem[]** parameter.<br /><br /> Specifies the source [!INCLUDE[TLA2#tla_xaml](../reference/includes/tla2sharptla_xaml_md.md)] files to include for UID checking, updating, or removing.|  
|`Task`|Required **String** parameter.<br /><br /> Specifies the UID management task that you want to perform. Valid options are **Check**, **Update**, or **Remove**.|  
  
## Example  
 The following example uses the \<xref:Microsoft.Build.Tasks.Windows.UidManager> task to check that the specified source [!INCLUDE[TLA2#tla_xaml](../reference/includes/tla2sharptla_xaml_md.md)] files contain [!INCLUDE[TLA2#tla_xaml](../reference/includes/tla2sharptla_xaml_md.md)] elements that have appropriate UIDs.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UidManagerTask">  
    <UidManager  
      Task="Check"  
      MarkupFiles="Page1.xaml;Page2.xaml"  
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />  
  </Target>  
</Project>  
```  
  
## See Also  
 [WPF MSBuild Reference](../reference/wpf-msbuild-reference.md)   
 [Task Reference](../reference/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../reference/msbuild-reference.md)   
 [Task Reference](../reference/msbuild-task-reference.md)   
 [Building a WPF Application (WPF)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [How to: Localize an Application](../Topic/How%20to:%20Localize%20an%20Application.md)