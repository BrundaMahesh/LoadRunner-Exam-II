/* -------------------------------------------------------------------------------
	Script Title       : 
	Script Description : 
                        
                        
	Recorder Version   : 0
   ------------------------------------------------------------------------------- */

vuser_init()
{

	web_set_sockets_option("SSL_VERSION", "AUTO");

	web_add_auto_header("Accept-Language", 
		"en-GB,en;q=0.9");

	web_url("petstore.octoperf.com", 
		"URL=https://petstore.octoperf.com/", 
		"Resource=0", 
		"RecContentType=text/html", 
		"Referer=", 
		"Snapshot=t1.inf", 
		"Mode=HTML", 
		LAST);

	/* Click on Enter the Store */

	lr_think_time(27);

/*Correlation comment - Do not change!  Original value='26DA05FCE45FCF96D564D487238FF056' Name ='jsessionid' Type ='ResponseBased'*/
	web_reg_save_param_regexp(
		"ParamName=jsessionid",
		"RegExp=JSESSIONID=(.*?);",
		SEARCH_FILTERS,
		"Scope=Cookies",
		"IgnoreRedirections=No",
		"RequestUrl=*/Catalog.action*",
		LAST);

	web_link("Enter the Store", 
		"Text=Enter the Store", 
		"Snapshot=t2.inf", 
		LAST);

	web_set_sockets_option("TLS_SNI", "0");
	
	
	//Image check
	web_image_check("JPetstore Logo","Src=../images/logo-topbar.gif",LAST);

	return 0;
}
