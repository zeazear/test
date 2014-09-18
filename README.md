else if(process.argv[2] === "trial" && process.argv.length === 3) {
async.series(
[
User.login,
function(callback) {
 request(rel('?sida=stan/stan'), function(e, r, b) {
 if(!e) {
 $ = cheerio.load(b);
 var imgaes = $('#body_area a').get();
 async.parallel(
 [
 function(callback) {
 isConfess(callback, rel($(images[0].find('img').attr('scr')))
 },
 function(callback) {
 isConfess(callback, rel($(images[1].find('img').attr('scr')))
 },
 function(callback) {
 isConfess(callback, rel($(images[2].find('img').attr('scr')))
 }
 ],
 function(err, results) {
 callback(null, "Confess: " + images[results.index0f(true)].attribs.href);
 }
 );
 }
 });
 },
 User.logout],
 function(err, results) {console.log(results.join(os.EOL));}
 );
 }
