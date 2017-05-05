
Here is a LESS file example showing detailed CSS style options:

color.less file example:
```less
@negative-color: #D11F38;
@positive-color: #72BF44;
@info-color: #727F85;
@neutral-color: #0081B9;
@line-color: #DEDEDE;
@line-color-light: #f1efeb;
@brand-color: #D30E7A;
@logo-mobile: "/static/images/logo-idibu.png";
@inactive-color: #E0E0E0;
@default-text-color: #000;
@happy-gray-dark: #4a4a4a;
@orange: #eb8b38;
@black: #000;
@neutral-color: #2b82bc;
@negative-color:#b65166;
@info-color:#888888;
@inactive-color:#DDDDDD;
@line-color:#efefef;
.bg-mixin() {
  background: #F5F5F5;
}

```


theme_confing.less file example:
```less

@crm-body-box-shadow : 2px 0px 5px -2px #bbb;
@crm-body-top : 1px;
@crm-body-right : 2px;
@crm-border : 'none';
/* page-title-1 h3 */
@page-title-color:  @black;
@page-title-ff: @fontRegular;
@page-title-fs: 14px;
@page-title-text-transform : uppercase;
/* page-title-2 (red-title) */
@page-title-2-color:@negative-color;
/* info-text-1 */
@page-info-color: @info-color;
@page-info-ff: @fontRegular;
@page-info-fs: 13px;
@page-info-text-transform : none;
/* info small */
@page-info-color-small:@info-color;
@page-info-ff-small:@fontRegular;
@page-info-fs-small: 12px;
@page-info-text-transform-small: none;
/* blue-link */
@page-link-color: @neutral-color;
@page-link-ff: @fontSemibold;
@page-link-fs: 13px;
@page-link-text-transform : none;
/* Label */
@page-label-color: @info-color;
@page-label-ff: @fontSemibold;
@page-label-fs: 13px;
@page-label-text-transform : none;
/* Black text */
@page-black-text-color: @black;
@page-black-text-ff: @fontRegular;
@page-black-text-fs: 13px;
@page-black-text-transform : none;
/* buttons styles*/
@btn-l-h: 34px;
@btn-text-transform: capitalize;
@btn-ff: @fontRegular;
@btn-f-size: 12px;
@btn-padding: 0px 15px;
@btn-width: 100%;
@btn-color: #fff;
@btn-b-radius: 5px;
/* buttons-arrow styles*/
@btn-arrow-right:10px;
@btn-arrow-fs: 18px;
@btn-arrow-lh: 36px;
/* buttons-colors styles*/
@color-theme-1:@positive-color;
@color-theme-2:@negative-color;
@color-theme-3:@neutral-color;
@color-theme-4:@inactive-color;
/* white buttons styles */
@white-btn-font-size: 13px;
@white-btn-ff: @fontSemibold;
@white-btn-border: 1px solid @line-color;
@white-btn-bg: #fff;
@white-btn-round : 3px;
@white-btn-color: @neutral-color;
/* select2-styles */
@select2-ff: @fontRegular;
@select2-fs: 13px;
@select2-height:28px;
@select2-color: #444;
@select2-border: 1px solid @line-color;
@select2-result-color: @neutral-color;
@select2-result-border: @neutral-color;
/* !IMPORTANT styles for caret can't be Should be selected on the basis of font size select height etc. */
@caret-border : @neutral-color transparent transparent;
@caret-border-width : 8px 8px 0;
@caret-m-left : -8px;
@caret-m-top: -3px;
/* / select2-styles */
/* input settings */
@input-height : 28px;
@input-ff : @fontRegular;
@input-fs : 13px;
@input-padding : 0 10px;
@input-color : @black;
///* BAR styles*/
@crm-bar-min-max-h: 50px;
@top-nav-active-color : @negative-color;
@crm-bar-top: 3px ;
@crm-bar-right: 2px;
@crm-bar-border : 'none';
@crm-bar-padding: 6px 30px 6px 15px;
///* nav styles*/
@crm-nav-border: solid @line-color;
@border-width : 1px;
@crm-nav-border-right : 1px solid @line-color;
@crm-nav-round : 3px;
@crm-nav-height : 36px;
@crm-nav-bg: #fff;
@nav-dropdown-font-size: 13px;
@nav-font-f: @fontRegular;
/* nav item 2 styles*/
@crm-nav-items-color:@inactive-color;
@crm-nav-items-fs: 22px;
@crm-nav-item-2-icon :'\e83f';
@crm-nav-item-2-font-size: @crm-nav-items-fs;
@crm-nav-item-2-color: @crm-nav-items-color;
/* nav item 3 styles*/
@crm-nav-item-3-icon : '\e842';
@crm-nav-item-3-font-size:  @crm-nav-items-fs;
@crm-nav-item-3-color: @crm-nav-items-color;
/* nav item 4 styles*/
@crm-nav-item-4-icon : '\e83e';
@crm-nav-item-4-font-size:  @crm-nav-items-fs;
@crm-nav-item-4-color: @crm-nav-items-color;
/* nav item 4 DropDownSelect styles*/
@select-height: 34px;
@select-width: 100px;
/* NavBar People NAV styles*/
  /* Avatar*/
  @crm-profile-avatar-w: 34px;
  @crm-profile-avatar-h: 34px;
  /* People Name*/
  @crm-profile-title-f-size: 14px ;
  @crm-profile-title-f-family: @fontSemibold;
  /* Edit Link*/
  @crm-profile-edit-f-size: 12px ;
  @crm-profile-edit-f-family: @fontRegular;
  /* Status Filter*/
    /* Item 1 */
    @crm-status-size-main: 28px;
    @crm-status-item-1-icon : '\e819';
    @crm-status-item-1-font-size: @crm-status-size-main;
    @crm-status-item-1-color: @positive-color;
    /* Item 2 */
    @crm-status-item-2-icon : '\e810';
    @crm-status-item-2-font-size: @crm-status-size-main;
    @crm-status-item-2-color: @orange;
    /* Item 3 */
    @crm-status-item-3-icon : '\e806';
    @crm-status-item-3-font-size: @crm-status-size-main;
    @crm-status-item-3-color: @negative-color;
    /* Item 4 */
    @crm-status-item-4-icon : '\e80b';
    @crm-status-item-4-font-size: 29px;
    @crm-status-item-4-color: @line-color;
  /* /Status Filter*/
  /* Profile Controls*/
    /* Item 1 */
    @crm-controls-size-main : 28px;
    @crm-controls-item-1-icon : '\e80e';
    @crm-controls-item-1-font-size: @crm-controls-size-main;
    @crm-controls-item-1-color: @line-color;
    /* Item 2 */
    @crm-controls-item-2-icon : '\e810';
    @crm-controls-item-2-font-size: @crm-controls-size-main;
    @crm-controls-item-2-color: @line-color;
    /* Item 3 */
    @crm-controls-item-3-icon : '\e806';
    @crm-controls-item-3-font-size: @crm-controls-size-main;
    @crm-controls-item-3-color: @line-color;
    /* Item 4 */
    @crm-controls-item-4-icon : '\e843';
    @crm-controls-item-4-font-size: @crm-controls-size-main;
    @crm-controls-item-4-color: @line-color;
    /* Item 5 */
    @crm-controls-item-5-icon: '\e844';
    @crm-controls-item-5-font-size: 30px;
    @crm-controls-item-5-color: @line-color;
  /* /Profile Controls*/
  /* Pager*/
    @crm-pager-border: 1px solid @line-color;
    @crm-pager-corners: 3px;
    /* next */
    @crm-pager-next-icon:'\e841';
    @crm-pager-next-size: 24px;
    @crm-pager-next-color: @neutral-color;
    /* prev */
    @crm-pager-prev-icon:'\e840';
    @crm-pager-prev-size: 24px;
    @crm-pager-prev-color: @neutral-color;
  /* /Pager*/
  
```
