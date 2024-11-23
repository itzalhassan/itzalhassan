public class AuthService {
    private Database db; // فرضية وجود اتصال قاعدة بيانات

    public User login(String username, String password) {
        User user = db.findUserByUsername(username);
        if (user != null && user.getPassword().equals(password)) {
            return user;
        }
        throw new IllegalArgumentException("Invalid credentials");
    }

    public void register(String username, String password, boolean isCelebrity) {
        User user = new User();
        user.setUsername(username);
        user.setPassword(password);
        user.setIsCelebrity(isCelebrity);
        db.saveUser(user);
    }
}
