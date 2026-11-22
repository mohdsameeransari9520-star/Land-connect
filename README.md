LandConnect – Real-Time Land Marketplace Mobile Application
​LandConnect is a mobile-first, real-time land marketplace prototype featuring a clean, modern messaging-inspired UI, role-based access control, interactive geolocation mapping, 24/7 cloud-synced property listings, real-time messaging, and private in-app WebRTC audio and video calling without exposing personal phone numbers.
​Key Features Implemented
​1. User Authentication and Role-Based Access Control (RBAC)
​Single-Step Login with Permanent Identity: Users log in with Name, Email, Password, and Role (Buyer, Seller, or Broker).
​Deterministic Fixed IDs (lc-XXXX): Each user's email generates a permanent, non-changing private LandConnect ID stored in a triple-layer local vault (IndexedDB + localStorage + Cookie), ensuring sessions persist across app restarts.
​Role Permissions:
​Buyers: Browse real-time land listings, explore interactive map pins, join meeting rooms, chat, and place private audio/video calls.
​Sellers and Brokers: Full CRUD access to publish, edit, geotag, and delete land listings globally, plus host live negotiation rooms.
​2. Community and 24/7 Cloud-Synced Land Listings
​Real-time property feed with category filtering (Residential, Agricultural, Commercial, Highway) and instant search by location, title, or plot size.
​Powered by retained MQTT over WebSockets, ensuring newly posted listings remain live 24/7 across all devices even after the lister logs out.
​3. Interactive Maps and Geolocation
​Built with Leaflet.js and OpenStreetMap.
​Displays interactive pins for every listed plot with quick preview cards and live GPS user location tracking.
​Sellers and Brokers can pin exact coordinates on an interactive map picker or capture live GPS coordinates when listing land.
​4. Real-Time Messaging and Cloud Meeting Rooms
​Dual-Path Delivery (WebRTC P2P DataChannels + MQTT Cloud Sync): Supports real-time text messages, voice notes, compressed photo sharing, live GPS location pins, typing indicators, sent/delivered/read ticks, reactions, quoted replies, and Delete for Everyone.
​24/7 Cloud User Directory and Offline Inbox: Users remain discoverable even when offline; messages and missed call alerts queue in the cloud inbox and deliver automatically when the recipient opens the app.
​Multi-User Meeting Rooms: Create or join shared room IDs (room-XXXX) where Buyers, Sellers, and Brokers can negotiate together.
​5. Private In-App Audio and Video Calling
​Zero Phone Number Exposure: All audio and video calls connect strictly via private lc-XXXX IDs using PeerJS (WebRTC MediaStreams).
​Full Call Lifecycle: Includes synthetic ringtone, interactive Swipe-to-Answer / Swipe-to-Decline incoming call screen, live call timer, microphone mute/unmute, camera toggle, front/back camera switching, instant <100ms hangup signaling, and persistent call history.
​6. Privacy and Access Controls
​Personal phone numbers are never collected or displayed.
​In-app toggles allow users to control incoming call permissions and read receipts.
​Technology Stack and Architectural Rationale
​Frontend and Mobile Packaging: HTML5, Tailwind CSS, Vanilla JavaScript (Single-File Mobile-First Architecture) packaged as an installable Android .apk via WebView wrapper and hosted live on GitHub Pages (HTTPS).
​Real-Time Audio/Video and P2P Data: PeerJS (WebRTC) for low-latency device-to-device media streams and data channels.
​24/7 Cloud Sync and Signaling: MQTT.js (wss://) for retained global listings, user presence directory, offline message inbox, and instant call signaling.
​Maps and Geolocation: Leaflet.js + OpenStreetMap + HTML5 Geolocation API.
​Persistent Client Storage: IndexedDB backed by localStorage and cookies for reliable session persistence inside Android WebView.
​Why this stack? To deliver a fast, zero-backend-cost, cross-platform functional prototype (both installable Android APK and live HTTPS web app) within the 5-day timeline while ensuring real two-device WebRTC audio/video calling and 24/7 global state synchronization without server cold-start delays.
​How to Run and Test
​Option A: Android APK
​1. Install LandConnect.apk on two Android devices (allow Camera, Microphone, and Location permissions when prompted).
​2. Log in on Device A as Seller (e.g., seller@test.com) and Device B as Buyer (e.g., buyer@test.com).
​3. Post a land listing on Device A—it immediately appears on Device B's Listings and Map tabs.
​4. Copy Device A's permanent ID (lc-XXXX) from the top bar, tap Connect ID on Device B, and test live chat, voice notes, audio call, and video call.
​Option B: Run Locally or via GitHub Pages
