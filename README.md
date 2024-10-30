# filmbrainz-seed
Following on from this thread (https://community.metabrainz.org/t/filmbrainz-ideas-thread-i-e-moviebrainz-videobrainz-etc/707370/11) I am creating this repository as a means to record information about various home media releases I own in a semi-structured format so that I can potentially add them later to the project when it is developed.

# General Objective
The general objective here is to try and capture as much metadata from the phyiscal media release that might be useful to contribute at a later date to a database built for cataloguing home media releases.

This micro-project should try and stay focused and so will only be capturing metadata about the various properties of home media (e.g. DVD, VHS) that is publicly available. All data should be sourced from a physical item and not duplicated or scraped from other sources (including other projects, databases, libaries, books etc.).

Due to this narrow focus, the project will not be capturing information about the filmed content itself (such as cast information, premiere dates, film type etc.). If applicable the item may include links to existing entries about the filmed content contained within that exist already in public databases (e.g. IMDb, Wikipedia etc.).

# Influences
There are some strong influences on what properties and how I would like to structure the metadata. With the intention that this will be eventually be for a "*brainz" project I will be liberally borrowing terminology and structure mentality from their existing products such as MusicBrainz and Bookbrainz.

I was also involved in a previous sub-project spun off by Discogs called Filmogs (filmo.gs, later films.discogs.com) as a contributor. Unfortunately Discogs decided to pull the plug on that project 31st August 2020 and all of the contributed data is considered to be lost (aside from stuff that was captured via the Internet Archive's WayBackMachine).

I will be combining the influences of both of these projects in the decisions I make with this personal micro-project.

# Captured Properties
Each "item" should have the following properties captured within it, of course if the property doesn't apply or exist on the physical item being processed it will be left as a null or empty value.

Packaging Attributes
This is a section that concerns itself with properties about the packaging.

- **Title** this is the title as it is printed on the item. If the title differentiates on different parts of the release (e.g. the title on the spine is different to the cover) then titles are to be seperated with " | " and a descriptor of where that title variation appears in square brackets "[]".
- **ETI** acronym for extra-title information, this is a field where you can store any additional title information. For example "Collector's Edition" or "Director's Cut".
- **Format** the format of the release (e.g. DVD, VHS, Blu-ray)
- **Format Detail** a more detailed description of the format, if it can be ascertained (e.g. DVD5, DVD9)
- **Packaging Format** a description value of the type of packaging the media was released in (e.g. DVD Keepcase), if not known then this field should read "unknown".
- **Packaging Notes** any notes about the packaging that might be of note such as dimensions, weight, material.
- **Label** previously known as "brand" on Filmogs, this is the general imprint featured predominately on the packaging (e.g. Universal, Warner Home Video)
- **Companies** stored as an array, a table of companies who were involved with the production of this home media. Can include copyright holders, distributors, manufacturers. Can include years if clearly stated.
- **GTIN** often simply referred to as "barcode", Global Trade Item Numbers often appear on home media when they are to be sold in retail outlets. This field should contain the numerical information as it is printed on the release, it should be prefixed with the standard of GTIN (e.g. EAN:3259190389397)
- **Identifiers** any identifiers that may appear on the packaging, the descriptions of these are a point of contention usually as they seemingly don't have an official name a lot of the time. Some examples of identifiers in this field would be "part numbers" which are alphanumerical sequences that may appear along the sides or bottom of parts of the packaging, BBFC certification references that are unique to British releases and often appear on the media label itself, matrix data which are alphanumerical strings that appear around the hub on the read-side of most optical mediums. Any metadata in this property should be structured [type][value][comment] where [type] might be a value such as "Part Number" [value] might be a value such as [DVD 903 893 9 ● 11] and [comment] might be a value such as Sleeve.
- **Language** the language(s) present on the release packaging.
- **Script** the script(s) present on the release packaging.
- **Release Territory** an educated guess as to the territory/country in which the item was released. If not known set to unknown.
- **Region** for releases that use the region system (i.e. DVD and Blu-ray) what region code the release falls under.
- **Classification** the classification(s) printed on the packaging. The format of this metadata should be [Classification Board]:[Rating] for example "BBFC:15".
- **Annotation** any important or interesting notes or comments about the packaging attributes that might need further explanation.

Content Attributes
This is a section that concerns itself with the properties about the audiovisual content contained on the item.
- **Color Mode** what color mode the content is presented in (e.g. Color, Black and White, Sepia), if mixed then list all used
- **Video Format** previously known as Colour Encoding, this is the television format the content is presented in (e.g. PAL, NTSC, SECAM)
- **Aspect Ratio** the aspect ratio of the audiovisual content (e.g. 16:9 Widescreen or 1.85:1 Anamorphic)
- **Languages Present** what languages are present for the audiovisual content on the release, with a descriptor prefix if it is an audio track or subtitle track and a comments suffix (e.g. Audio Track:English:Default,Subtitle Track:English HoH:Burnt In - Main Feature,Audio Track:English:Commentary).
- **Audio Format** the audio formats that are present for the audiovisual content on the release, in the format [Description][Format] (e.g. English:Dolby Digital 2.0)
- **Runtime** the printed run-time of the audiovisual content in mins, if not listed then this value should be left null.

Title Layout
This is a section that concerns itself with the layout of the audiovisual content on the media. It should be recorded as how that media would appear if played in a traditional player (e.g. DVD player).
- **Position** a numerical value that indicates the order in which the content would appear
- **Description** Short description of the title, is it the main feature, an epsiode, a bonus feature, ident, trailer, advert, still image etc.
- **Duration** the duration in hh:mm:ss of the title, for analogue medium this will be an approximation
- **Chapters** a list of the chapters (if present)
- **Audio Tracks** a description of the audio tracks available in this title