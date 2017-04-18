# Pusher-Java-HTTP-Auth
Server-side authorisation of a device on a Pusher private channel

# Java Dropwizard implementation of Pusher client auth on private channel

    // Authorise a user on a private channel
    @Consumes(MediaType.WILDCARD)
    @POST
    @Path("/auth")
    public Response auth(String requestBody) {
        String channelName = requestBody.substring(requestBody.indexOf("private-"), requestBody.indexOf('&'));
        String socketId = requestBody.substring(requestBody.indexOf("socket_id=")+10, requestBody.length());
        String auth = pusher.authenticate(socketId, channelName);
        return Response.ok(auth).build();
    }
