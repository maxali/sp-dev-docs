---


manager: soliver
ms.date: 9/16/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d64d36be-8a19-6fd8-2798-0cbac949649b
---

![Collapse
section](../icons/collapse_all.gif "Collapse section")![Expand
section](../icons/expand_all.gif "Expand section")![](../icons/collapse_all.gif)![](../icons/expand_all.gif)![](../icons/dropdown.gif)![](../icons/dropdownHover.gif)![Copy
code](../icons/copycode.gif "Copy code")![Copy code
hover](../icons/copycodeHighlight.gif "Copy code hover")
<table>
<tbody>
<tr class="odd">
<td align="left"></td>
</tr>
</tbody>
</table>

Visual Basic  
C\#  
C++  
JavaScript  

<table>
<tbody>
<tr class="odd">
<td align="left"><span id="runningHeaderText"></span></td>
</tr>
<tr class="even">
<td align="left"># Schema map (AppHostWebFeatures)</td>
</tr>
<tr class="odd">
<td align="left"><span id="headfeedbackarea" class="feedbackhead"><a href="javascript:SubmitFeedback(&#39;docthis@Microsoft.com&#39;,&#39;&#39;,&#39;&#39;,&#39;&#39;,&#39;1.0.18082.1225&#39;,&#39;%0\dThank%20you%20for%20your%20feedback.%20The%20developer%20writing%20teams%20use%20your%20feedback%20to%20improve%20documentation.%20While%20we%20are%20reviewing%20your%20feedback,%20we%20may%20send%20you%20e-mail%20to%20ask%20for%20clarification%20or%20feedback%20on%20a%20solution.%20We%20do%20not%20use%20your%20e-mail%20address%20for%20any%20other%20purpose%20and%20we%20delete%20it%20after%20we%20finish%20our%20review.%0\AFor%20further%20information%20about%20the%20privacy%20policies%20of%20Microsoft,%20please%20see%20http://privacy.microsoft.com/en-us/default.aspx.%0\A%0\d&#39;,&#39;Customer%20feedback&#39;);">Send feedback</a></span></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col width="100%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"></td>
</tr>
</tbody>
</table>

**Last modified:** September 16, 2015

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><img src="../icons/alert_note.gif" title="Note" alt="Note" /><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>The string &quot;app&quot; appears as part, or all, of some element, attribute, and file names because SharePoint Add-ins were originally called &quot;apps for SharePoint&quot;. To ensure backward compatibility, the schemas have not been changed.</p></td>
</tr>
</tbody>
</table>

This topic shows the schema definition for **AppHostWebFeatures**.

<span codelanguage="xmlLang"></span>
XML 
<span class="copyCode" onclick="CopyCode(this)"
onkeypress="CopyCode_CheckKey(this, event)"
onmouseover="ChangeCopyCodeIcon(this)"
onmouseout="ChangeCopyCodeIcon(this)" tabindex="0">![Copy
code](../icons/copycode.gif "Copy code")Copy code</span>
    <?xml version="1.0" encoding="utf-8"?>
    <xs:schema id="WSS" targetNamespace="http://schemas.microsoft.com/sharepoint/" elementFormDefault="qualified" xmlns="http://schemas.microsoft.com/sharepoint/" xmlns:mstns="http://schemas.microsoft.com/sharepoint/" xmlns:xs="http://www.w3.org/2001/XMLSchema" version="1.0" attributeFormDefault="unqualified">  
      <xs:include id="CoreDefinitions" schemaLocation="coredefinitions.xsd" />
      <xs:include id="CommandUI" schemaLocation="cui.xsd" />

      <xs:complexType name="FeatureDefinition">
        <xs:all>
          <xs:element name="ElementManifests" type="ElementManifestReferences" minOccurs="0" maxOccurs="1" />
          <xs:element name="Properties" type="FeaturePropertyDefinitions" minOccurs="0" maxOccurs="1" />
          <xs:element name="ActivationDependencies" minOccurs="0" maxOccurs="1" type="FeatureActivationDependencyDefinitions" />
          <xs:element name="UpgradeActions" minOccurs="0" maxOccurs="1" type="UpgradeActionsDefinition" />
        </xs:all>
        <xs:attribute name="Id" type="UniqueIdentifier" use="required" />
        <xs:attribute name="Title" type="LocalizableString" />
        <xs:attribute name="Description" type="LocalizableString" />
        <xs:attribute name="Version" type="FeatureVersion" />
        <xs:attribute name="Scope" type="FeatureScope" use="required" />
        <xs:attribute name="ReceiverAssembly" type="AssemblyStrongName" />
        <xs:attribute name="ReceiverClass" type="AssemblyClass" />
        <xs:attribute name="Creator" type="LocalizableString" />
        <xs:attribute name="DefaultResourceFile" type="xs:string" />
        <xs:attribute name="Hidden" type="TRUEFALSE" />
        <xs:attribute name="SolutionId" type="UniqueIdentifier" />
        <xs:attribute name="ActivateOnDefault" type="TRUEFALSE" />
        <xs:attribute name="AutoActivateInCentralAdmin" type="TRUEFALSE" />
        <xs:attribute name="AlwaysForceInstall" type="TRUEFALSE" />
        <xs:attribute name="RequireResources" type="TRUEFALSE" />
        <xs:attribute name="ImageUrl" type="RelativeFilePath" use="optional" />
        <xs:attribute name="ImageUrlAltText" type="LocalizableString" use="optional" />
        <xs:attribute name="UIVersion" type="UIVersion" />
      </xs:complexType>
      <xs:simpleType name="FeatureVersion">
        <xs:restriction base="xs:string">
          <xs:pattern value="\d+\.\d+\.\d+\.\d+" />
        </xs:restriction>
      </xs:simpleType>
      <xs:element name="Feature" type="FeatureDefinition">
      </xs:element>
      <xs:complexType name="ElementManifestReference">
        <xs:sequence>
        </xs:sequence>
        <xs:attribute name="Location" type="RelativeFilePath" use="required" />
      </xs:complexType>
      <xs:complexType name="ElementManifestReferences">
        <xs:sequence>
          <xs:choice minOccurs="0" maxOccurs="unbounded">
            <xs:element name="ElementManifest" type="ElementManifestReference" minOccurs="0" maxOccurs="unbounded" />
            <xs:element name="ElementFile" type="ElementManifestReference" minOccurs="0" maxOccurs="unbounded" />
          </xs:choice>
        </xs:sequence>
      </xs:complexType>
      <xs:element name="Elements" type="ElementDefinitionCollection">
      </xs:element>
       <xs:complexType name="CommandUIExtensionType">
        <xs:sequence>
          <xs:element name="CommandUIDefinitions" type="CommandUIDefinitionsType" minOccurs="0" maxOccurs="1" />
          <xs:element name="CommandUIHandlers" type="CommandUIHandlersType" minOccurs="0" maxOccurs="1" />
        </xs:sequence>
      </xs:complexType>
      <xs:complexType name="CommandUIDefinitionsType">
        <xs:sequence>
          <xs:element name="CommandUIDefinition" type="CommandUIDefinitionType" minOccurs="1" maxOccurs="unbounded" />
        </xs:sequence>
      </xs:complexType>
      <xs:complexType name="CommandUIHandlersType">
        <xs:sequence>
          <xs:element name="CommandUIHandler" type="CommandUIHandlerType" minOccurs="1" maxOccurs="unbounded" />
        </xs:sequence>
      </xs:complexType>
      <xs:complexType name="CommandUIHandlerType" mixed="true">
        <xs:sequence />
        <xs:attribute name="Command" type="xs:string" use="required" />
        <xs:attribute name="CommandAction" type="xs:string" use="required" />
        <xs:attribute name="EnabledScript" type="xs:string" use="optional" />
      </xs:complexType>
      <xs:complexType name="CommandUIDefinitionType" mixed="true">
        <xs:choice minOccurs="0" maxOccurs="1">
          <xs:element name="Button" type="ButtonType" />
          <xs:element name="CheckBox" type="CheckBoxType" />
          <xs:element name="ComboBox" type="ComboBoxType" />
          <xs:element name="ColorPicker" type="ColorPickerType" />
          <xs:element name="ContextualGroup" type="ContextualGroupType" />
          <xs:element name="ContextualTabs" type="ContextualTabsType" />
          <xs:element name="Controls" type="ControlsType" />
          <xs:element name="DropDown" type="DropDownType" />
          <xs:element name="FlyoutAnchor" type="FlyoutAnchorType" />
          <xs:element name="Gallery" type="GalleryType" />
          <xs:element name="GalleryButton" type="GalleryButtonType" />
          <xs:element name="GroupTemplate" type="GroupTemplateType" />
          <xs:element name="Group" type="GroupType" />
          <xs:element name="Groups" type="GroupsType" />
          <xs:element name="InsertTable" type="InsertTableType" />
          <xs:element name="Label" type="LabelType" />
          <xs:element name="MRUSplitButton" type="MRUSplitButtonType" />
          <xs:element name="MaxSize" type="MaxSizeType" />
          <xs:element name="Menu" type="MenuType" />
          <xs:element name="MenuSection" type="MenuSectionType" />
          <xs:element name="QAT" type="QATType" />
          <xs:element name="Ribbon" type="RibbonType" />
          <xs:element name="Scale" type="ScaleType" />
          <xs:element name="Scaling" type="ScalingType" />
          <xs:element name="Spinner" type="SpinnerType" />
          <xs:element name="SplitButton" type="SplitButtonType" />
          <xs:element name="Tab" type="TabType" />
          <xs:element name="Tabs" type="TabsType" />
          <xs:element name="TextBox" type="TextBoxType" />
          <xs:element name="ToggleButton" type="ToggleButtonType" />
        </xs:choice>
        <xs:attribute name="Location" type="xs:string" use="required" />
      </xs:complexType>
      <xs:complexType name="CustomActionDefinition" mixed="true">
        <xs:all>
          <xs:element name="UrlAction" type="UrlActionDefinition" minOccurs="0" maxOccurs="1" />
          <xs:element name="CommandUIExtension" type="CommandUIExtensionType" minOccurs="0" maxOccurs="1" />
        </xs:all>
        <xs:attribute name="Description" type="LocalizableString" />
        <xs:attribute name="Id" type="UniqueIdentifier" />
        <xs:attribute name="ImageUrl" type="LocalizableString" />
        <xs:attribute name="Location" type="CustomActionLocations" use="optional" />
        <xs:attribute name="RegistrationType" type="CustomActionRegistrationType" />
        <xs:attribute name="RegistrationId" type="xs:string" />
        <xs:attribute name="RequireSiteAdministrator" type="TRUEFALSE" />
        <xs:attribute name="Rights" type="xs:string" />
        <xs:attribute name="Sequence" type="Sequence" />
        <xs:attribute name="ShowInReadOnlyContentTypes" type="TRUEFALSE" />
        <xs:attribute name="ShowInSealedContentTypes" type="TRUEFALSE" />
        <xs:attribute name="Title" type="LocalizableString" />
        <xs:attribute name="UIVersion" type="UIVersion" />
        <xs:attribute name="HostWebDialog" type="TRUEFALSE"  use="optional" />
        <xs:attribute name="HostWebDialogHeight" type="xs:int"  use="optional" />
        <xs:attribute name="HostWebDialogWidth" type="xs:int"  use="optional" />
      </xs:complexType>
      <xs:complexType name="UrlActionDefinition">
        <xs:sequence>
        </xs:sequence>
        <xs:attribute name="Url" type="AbsoluteOrRelativeUrl" use="required" />
      </xs:complexType>
      <xs:simpleType name="CustomActionRegistrationType">
        <xs:restriction base="xs:string">
          <xs:enumeration value="List" />
          <xs:enumeration value="ContentType" />
          <xs:enumeration value="FileType" />
          <xs:enumeration value="ProgId" />
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType name="CustomActionLocations">
        <xs:restriction base="xs:string">
          <xs:enumeration value="CommandUI.Ribbon" />
          <xs:enumeration value="EditControlBlock" />
        </xs:restriction>
      </xs:simpleType>
      <xs:complexType name="CustomActionDefinitions">
        <xs:sequence>
          <xs:element name="CustomAction" type="CustomActionDefinition" minOccurs="1" maxOccurs="unbounded" />
        </xs:sequence>
      </xs:complexType>
      <xs:complexType name="FeatureActivationDependencyDefinition">
        <xs:sequence>
        </xs:sequence>
        <xs:attribute name="FeatureId" type="UniqueIdentifier" use="required" />
        <xs:attribute name="MinimumVersion" type="FeatureVersion" use="optional" />
        <xs:attribute name="SolutionId" type="UniqueIdentifier" use="optional" />
        <xs:attribute name="SolutionTitle" type="xs:string" use="optional" />
        <xs:attribute name="SolutionName" type="xs:string" use="optional" />
        <xs:attribute name="SolutionUrl" type="xs:string" use="optional" />
        <xs:attribute name="FeatureTitle" type="xs:string" use="optional" />
        <xs:attribute name="FeatureDescription" type="xs:string" use="optional" />
      </xs:complexType>
      <xs:complexType name="FeatureActivationDependencyDefinitions">
        <xs:sequence>
          <xs:element name="ActivationDependency" type="FeatureActivationDependencyDefinition" minOccurs="0" maxOccurs="unbounded" />
        </xs:sequence>
      </xs:complexType>
      <xs:complexType name="FeatureTemplateReference">
        <xs:sequence>
          <xs:element name="Properties" type="FeaturePropertyDefinitions" minOccurs="0" maxOccurs="1" />
        </xs:sequence>
        <xs:attribute name="ID" type="UniqueIdentifier" use="required" />
        <xs:attribute name="Name" type="xs:string" use="optional" />
        <xs:attribute name="SourceVersion" type="FeatureVersion" use="optional" />
      </xs:complexType>
      <xs:complexType name="FeatureTemplateReferences">
        <xs:sequence>
          <xs:element name="Feature" type="FeatureTemplateReference" minOccurs="0" maxOccurs="unbounded" />
        </xs:sequence>
      </xs:complexType>
      <xs:complexType name="VersionRangeDefinition">
        <xs:sequence minOccurs="0" maxOccurs="unbounded">
          <xs:group ref="UpgradeActionsGroup" />
        </xs:sequence>
        <xs:attribute name="BeginVersion" type="FeatureVersion" use="optional" />
        <xs:attribute name="EndVersion" type="FeatureVersion" use="optional" />
      </xs:complexType>
      <xs:complexType name="UpgradeActionsDefinition">
        <xs:choice minOccurs="0" maxOccurs="unbounded">
          <xs:element name="VersionRange" type="VersionRangeDefinition" minOccurs="0" maxOccurs="unbounded" />
          <xs:group ref="UpgradeActionsGroup" />
        </xs:choice>
        <xs:attribute name="ReceiverAssembly" type="AssemblyStrongName" use="optional" />
        <xs:attribute name="ReceiverClass" type="AssemblyClass" use="optional" />
      </xs:complexType>
      <xs:group name="UpgradeActionsGroup">
        <xs:choice>
           <xs:element name="ApplyElementManifests" type="ElementManifestReferences" minOccurs="0" maxOccurs="unbounded" />
        </xs:choice>
      </xs:group>

      <xs:complexType name="FeaturePropertyDefinitions">
        <xs:sequence>
          <xs:element name="Property" type="FeaturePropertyDefinition" minOccurs="0" maxOccurs="unbounded" />
        </xs:sequence>
      </xs:complexType>
      <xs:complexType name="FeaturePropertyDefinition">
        <xs:sequence>
        </xs:sequence>
        <xs:attribute name="Key" type="xs:string" />
        <xs:attribute name="Value" type="xs:string" />
      </xs:complexType>

      <xs:complexType name="SimplePropertyDefinition">
        <xs:simpleContent>
          <xs:extension base="xs:string">
            <xs:attribute name="Name" type="xs:string" />
          </xs:extension>
        </xs:simpleContent>
      </xs:complexType>
      <xs:simpleType name="PropertyBagType">
        <xs:restriction base="xs:string">
          <xs:enumeration value="int" />
          <xs:enumeration value="string" />
          <xs:enumeration value="DateTime" />
        </xs:restriction>
      </xs:simpleType>
      <xs:complexType name="PropertyValueAttributeDefinition">
        <xs:simpleContent>
          <xs:extension base="xs:string">
            <xs:attribute name="Name" type="xs:string" />
            <xs:attribute name="Value" type="xs:string" />
            <xs:attribute name="Type" type="PropertyBagType" use="optional" />
          </xs:extension>
        </xs:simpleContent>
      </xs:complexType>

      <xs:complexType name="PropertyBagDefinition">
        <xs:sequence>
          <xs:element name="Property" type="PropertyValueAttributeDefinition" minOccurs="0" maxOccurs="unbounded" />
        </xs:sequence>
        <xs:attribute name="ItemIndex" type="xs:string" use="optional" />
        <xs:attribute name="Url" type="xs:string" use="optional" />
        <xs:attribute name="ParentType" type="PropertyBagParentTypeDefinition" use="required" />
        <xs:attribute name="RootWebOnly" type="TRUEFALSE" use="optional" />
        <xs:attribute name="HyperlinkBaseUrl" type="AbsoluteUrl" use="optional" />
      </xs:complexType>
      <xs:simpleType name="PropertyBagParentTypeDefinition">
        <xs:restriction base="xs:string">
          <xs:enumeration value="Web" />
          <xs:enumeration value="Folder" />
          <xs:enumeration value="ListItem" />
          <xs:enumeration value="File" />
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType name="UIVersion">
        <xs:restriction base="xs:string" />
      </xs:simpleType>
      <xs:complexType name="ClientWebPartDefinition">
        <xs:all>
          <xs:element name="Content" type="ClientWebPartDefinitionContent" minOccurs="1" maxOccurs="1" />
          <xs:element name="Properties" type="ClientWebPartProperties" minOccurs="0" maxOccurs="1" />
        </xs:all>
        <xs:attribute name="Name" type="xs:string" use="required" />
        <xs:attribute name="DefaultWidth" type="xs:int"  use="optional"/>
        <xs:attribute name="DefaultHeight" type="xs:int" use="optional" />
        <xs:attribute name="Title" type="xs:string" use="optional" />
        <xs:attribute name="Description" type="xs:string" use="optional" />
      </xs:complexType>
      <xs:complexType name="ClientWebPartDefinitionContent">
        <xs:attribute name="Type" type="ClientWebPartDefinitionContentType" use="required" />
        <xs:attribute name="Src" type="xs:string" use="optional" />
      </xs:complexType>
      <xs:simpleType name="ClientWebPartDefinitionContentType">
        <xs:restriction base="xs:string">
          <xs:enumeration value="html" />
        </xs:restriction>
      </xs:simpleType>
      <xs:complexType name="ClientWebPartProperties">
        <xs:sequence>
          <xs:element name="Property" type="ClientWebPartProperty"  minOccurs="0" maxOccurs="unbounded" />
        </xs:sequence>
      </xs:complexType>
      <xs:complexType name="ClientWebPartProperty">
        <xs:all>
          <xs:element name="EnumItems" type="ClientWebPartEnumItems" minOccurs="0" maxOccurs="1" />
        </xs:all>
        <xs:attribute name="Name" type="xs:string" use="required" />
        <xs:attribute name="Type" type="ClientWebPartPropertyType" use="required" />
        <xs:attribute name="RequiresDesignerPermission" type="xs:boolean"  use="required" />
        <xs:attribute name="DefaultValue" type="xs:string" use="required" />
        <xs:attribute name="PersonalizationScope" type="WebPartPersonalizationScope" use="optional" />
        <xs:attribute name="PersonalizableIsSensitive" type="xs:boolean" use="optional" />
        <xs:attribute name="WebBrowsable" type="xs:boolean" use="optional" />
        <xs:attribute name="WebDisplayName" type="xs:string" use="optional" />
        <xs:attribute name="WebDescription" type="xs:string" use="optional" />
        <xs:attribute name="WebCategory" type="xs:string" use="optional" />
        <xs:attribute name="ManagedLinkFixup" type="xs:boolean" use="optional" />
        <xs:attribute name="ManagedLinkConvertServerLinksToRelative" type="xs:boolean" use="optional" />
        <xs:attribute name="Multilingual" type="xs:boolean" use="optional" />
      </xs:complexType>
      <xs:complexType name="ClientWebPartEnumItems">
        <xs:sequence>
          <xs:element name="EnumItem" type="ClientWebPartEnumItem"  minOccurs="0" maxOccurs="unbounded" />
        </xs:sequence>
      </xs:complexType>
      <xs:complexType name="ClientWebPartEnumItem">
        <xs:attribute name="Value" type="xs:string" use="required" />
        <xs:attribute name="WebDisplayName" type="xs:string" use="optional" />
      </xs:complexType>
      <xs:simpleType name="ClientWebPartPropertyType">
        <xs:restriction base="xs:string">
          <xs:enumeration value="string" />
            <xs:enumeration value="int" />
          <xs:enumeration value="boolean" />
          <xs:enumeration value="enum" />
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType name="WebPartPersonalizationScope">
        <xs:restriction base="xs:string">
          <xs:enumeration value="shared" />
          <xs:enumeration value="user" />
        </xs:restriction>
      </xs:simpleType>
      <xs:simpleType name="FeatureScope">
        <xs:restriction base="xs:string">
          <xs:enumeration value="Web" />
        </xs:restriction>
      </xs:simpleType>

      <xs:complexType name="ElementDefinitionCollection">
        <xs:sequence>
          <xs:choice minOccurs="0" maxOccurs="unbounded">
            <xs:element name="CustomAction" type="CustomActionDefinition" />
            <xs:element name="ClientWebPart" type="ClientWebPartDefinition" />
          </xs:choice>
        </xs:sequence>
        <xs:attribute name="Id" type="UniqueIdentifier" />
      </xs:complexType>

    </xs:schema>







