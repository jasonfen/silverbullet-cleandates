#meta

~~~space-script
// Registering the dateAdd function to add days to a date
silverbullet.registerFunction({ name: "dateAdd" }, (baseDate, daysToAdd) => {
  // Use today's date if baseDate is null or undefined
  if (!baseDate) {
    const today = Temporal.Now.plainDateISO();
    baseDate = today.toString();
  }
  
  try {
    const parsedBaseDate = Temporal.PlainDate.from(baseDate);
    const resultDate = parsedBaseDate.add({ days: daysToAdd });
    return resultDate.toString();
  } catch (error) {
    console.error("Error in dateAdd function:", error);
    return null;
  }
});

// Registering the CleanPN function
silverbullet.registerFunction({ name: "CleanPN" }, (pagename) => {
  const removeQuotesAndPrefix = (pageName) => pageName.replace(/^"|\*workdev\/journal\/|\"$/g, '');
  let cleanedPageName = removeQuotesAndPrefix(pagename);
  console.log("Cleaned Page Name:", cleanedPageName);
  return cleanedPageName;
});

// Function to get cleanedPagePre (previous day)
silverbullet.registerFunction({ name: "CleanPNPre" }, (pagename) => {
  let cleanedPageName = silverbullet.functions.CleanPN(pagename); // Clean the page name
  let cleanedPagePre = silverbullet.functions.dateAdd(cleanedPageName, -1); // Subtract 1 day
  console.log("Previous Day:", cleanedPagePre); // Log previous day
  return cleanedPagePre.toString();
});

// Function to get cleanedPageNxt (next day)
silverbullet.registerFunction({ name: "CleanPNNxt" }, (pagename) => {
  let cleanedPageName = silverbullet.functions.CleanPN(pagename); // Clean the page name
  let cleanedPageNxt = silverbullet.functions.dateAdd(cleanedPageName, 1); // Add 1 day
  console.log("Next Day:", cleanedPageNxt); // Log next day
  return cleanedPageNxt.toString();
});
~~~
