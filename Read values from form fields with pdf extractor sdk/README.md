## How to read values from form fields with pdf extractor sdk in VB.NET with ByteScout Data Extraction Suite

### Learn to code in VB.NET to read values from form fields with pdf extractor sdk with this step-by-step tutorial

These source code samples are assembled by their programming language and functions they apply. ByteScout Data Extraction Suite is the bundle that includes three SDK tools for data extraction from PDF, scans, images and from spreadsheets: PDF Extractor SDK, Data Extraction SDK, Barcode Reader SDK. It can be applied to read values from form fields with pdf extractor sdk using VB.NET.

This prolific sample source code in VB.NET for ByteScout Data Extraction Suite contains various functions and other necessary options you should do calling the API to read values from form fields with pdf extractor sdk. This VB.NET sample code is all you need for your app. Just copy and paste the code, add references (if needs to) and you are all set! Enjoy writing a code with ready-to-use sample VB.NET codes.

Trial version of ByteScout Data Extraction Suite is available for free. Source code samples are included to help you with your VB.NET app.

## REQUEST FREE TECH SUPPORT

[Click here to get in touch](https://bytescout.zendesk.com/hc/en-us/requests/new?subject=ByteScout%20Data%20Extraction%20Suite%20Question)

or just send email to [support@bytescout.com](mailto:support@bytescout.com?subject=ByteScout%20Data%20Extraction%20Suite%20Question) 

## ON-PREMISE OFFLINE SDK 

[Get Your 60 Day Free Trial](https://bytescout.com/download/web-installer?utm_source=github-readme)
[Explore SDK Docs](https://bytescout.com/documentation/index.html?utm_source=github-readme)
[Sign Up For Online Training](https://academy.bytescout.com/)


## ON-DEMAND REST WEB API

[Get your API key](https://pdf.co/documentation/api?utm_source=github-readme)
[Explore Web API Documentation](https://pdf.co/documentation/api?utm_source=github-readme)
[Explore Web API Samples](https://github.com/bytescout/ByteScout-SDK-SourceCode/tree/master/PDF.co%20Web%20API)

## VIDEO REVIEW

[https://www.youtube.com/watch?v=NEwNs2b9YN8](https://www.youtube.com/watch?v=NEwNs2b9YN8)




<!-- code block begin -->

##### ****Program.vb:**
    
```
Imports System.Xml
Imports Bytescout.PDFExtractor

Module Program

    Sub Main()

        Try
            ' Create XMLExtractor interface
            Using extractor As New XMLExtractor("demo", "demo")

                ' Load Sample PDF document
                extractor.LoadDocumentFromFile("filled_form.pdf")

                ' Get PDF document text as XML
                Dim xmlText As String = extractor.GetXML

                ' Load XML
                Dim xmlDocument As XmlDocument = New XmlDocument
                xmlDocument.LoadXml(xmlText)

                ' Select all "control" nodes
                Dim formControls As XmlNodeList = xmlDocument.SelectNodes("//control")
                If (Not (formControls) Is Nothing) Then
                    For Each formControl As XmlNode In formControls

                        Dim typeAttribute As XmlAttribute = formControl.Attributes("type")

                        ' Get filled textboxes
                        If (typeAttribute.Value = "editbox") Then
                            If Not String.IsNullOrEmpty(formControl.InnerText) Then
                                Console.WriteLine(("EDITBOX " + (formControl.Attributes("id").Value + (": " + formControl.InnerText))))
                            End If

                        End If

                        ' Get checked checkboxes
                        If (typeAttribute.Value = "checkbox") Then
                            If (formControl.Attributes("state").Value = "1") Then
                                Console.WriteLine(("CHECKBOX " _
                                    + (formControl.Attributes("id").Value + (": " + formControl.Attributes("state").Value))))
                            End If
                        End If

                    Next
                End If
            End Using

        Catch ex As Exception
            Console.WriteLine(ex.Message)
        End Try

        Console.WriteLine()
        Console.WriteLine("Press any key to exit...")
        Console.ReadLine()

    End Sub

End Module

```

<!-- code block end -->    

<!-- code block begin -->

##### ****ReadValuesFromFormFields.vbproj:**
    
```
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" Condition="Exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props')" />
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>
    <ProjectGuid>{1A9B710D-F645-41B2-8F9F-50A78416F161}</ProjectGuid>
    <OutputType>Exe</OutputType>
    <StartupObject>ReadValuesFromFormFields.Program</StartupObject>
    <RootNamespace>ReadValuesFromFormFields</RootNamespace>
    <AssemblyName>ReadValuesFromFormFields</AssemblyName>
    <FileAlignment>512</FileAlignment>
    <MyType>Console</MyType>
    <TargetFrameworkVersion>v2.0</TargetFrameworkVersion>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
    <PlatformTarget>AnyCPU</PlatformTarget>
    <DebugSymbols>true</DebugSymbols>
    <DebugType>full</DebugType>
    <DefineDebug>true</DefineDebug>
    <DefineTrace>true</DefineTrace>
    <OutputPath>bin\Debug\</OutputPath>
    <NoWarn>42016,41999,42017,42018,42019,42032,42036,42020,42021,42022</NoWarn>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
    <PlatformTarget>AnyCPU</PlatformTarget>
    <DebugType>pdbonly</DebugType>
    <DefineDebug>false</DefineDebug>
    <DefineTrace>true</DefineTrace>
    <Optimize>true</Optimize>
    <OutputPath>bin\Release\</OutputPath>
    <NoWarn>42016,41999,42017,42018,42019,42032,42036,42020,42021,42022</NoWarn>
  </PropertyGroup>
  <PropertyGroup>
    <OptionExplicit>On</OptionExplicit>
  </PropertyGroup>
  <PropertyGroup>
    <OptionCompare>Binary</OptionCompare>
  </PropertyGroup>
  <PropertyGroup>
    <OptionStrict>Off</OptionStrict>
  </PropertyGroup>
  <PropertyGroup>
    <OptionInfer>On</OptionInfer>
  </PropertyGroup>
  <ItemGroup>
    <Reference Include="Bytescout.PDFExtractor, Version=9.1.0.3170, Culture=neutral, PublicKeyToken=f7dd1bd9d40a50eb, processorArchitecture=MSIL">
      <SpecificVersion>False</SpecificVersion>
      <HintPath>c:\Program Files\Bytescout PDF Extractor SDK\net2.00\Bytescout.PDFExtractor.dll</HintPath>
    </Reference>
    <Reference Include="System" />
    <Reference Include="System.Data" />
    <Reference Include="System.Deployment" />
    <Reference Include="System.Xml" />
  </ItemGroup>
  <ItemGroup>
    <Import Include="Microsoft.VisualBasic" />
    <Import Include="System" />
    <Import Include="System.Collections" />
    <Import Include="System.Collections.Generic" />
    <Import Include="System.Data" />
    <Import Include="System.Diagnostics" />
  </ItemGroup>
  <ItemGroup>
    <Compile Include="Program.vb" />
  </ItemGroup>
  <Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />
</Project>
```

<!-- code block end -->